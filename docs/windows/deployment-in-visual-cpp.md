---
title: Nasazení ve Visual C++
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
ms.openlocfilehash: 67d5c7b0772eda55d1b653bd73f95ac93e31e644
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514818"
---
# <a name="deployment-in-visual-c"></a>Nasazení ve Visual C++

Instalace vaší aplikace na jiném počítači, než je vývojový počítač, se označuje jako *nasazení*. Když nasadíte vizuální C++ aplikaci na jiný počítač, musíte nainstalovat aplikaci i všechny soubory knihovny, na kterých závisí. Visual Studio umožňuje tři způsoby, jak nasadit knihovny C++ vizuálů společně s vaší aplikací: *centrální nasazení*, *místní nasazení*a *statické propojení*. Centrální nasazení umístí soubory knihovny do adresáře Windows, kde je služba web Windows Update může aktualizovat automaticky. Místní nasazení umístí soubory knihovny do stejného adresáře jako vaše aplikace. Všechny místně nasazené knihovny je potřeba znovu nasadit, aby je bylo možné aktualizovat. Statické propojení váže kód knihovny do aplikace. Je nutné znovu zkompilovat a znovu nasadit aplikaci, aby při použití statického propojení využila jakékoli aktualizace knihoven.

V aplikaci Visual Studio 2015 byla knihovna modulu runtime jazyka Microsoft C refaktored na součásti místní knihovny specifické pro danou verzi a nová knihovna univerzálního běhového prostředí jazyka C, která je nyní součástí systému Windows. Podrobnosti o nasazení univerzálního CRT naleznete v tématu [nasazení univerzálního CRT](universal-crt-deployment.md).

## <a name="central-deployment"></a>Centrální nasazení

V centrálním nasazení jsou soubory DLL knihovny nainstalovány v adresáři Windows\System32 nebo pro soubory knihovny 32 v systémech x64, adresář Windows\SysWow64. Společnost Microsoft automaticky aktualizuje knihovny, které jsou nasazeny centrálně. V případě C++ vizuálních knihoven, které jsou místně nasazeny nebo staticky propojeny, je nutné zadat aktualizace.

K centrálnímu nasazení vizuálních C++ knihoven můžete použít jeden z těchto dvou zdrojů k instalaci souborů:

- *Redistribuovatelné soubory balíčku* , což jsou spustitelné soubory samostatného příkazového řádku, které obsahují všechny vizuální C++ distribuovatelné knihovny v komprimované podobě nebo

- *Redistribuovatelné slučovací moduly* (soubory. msm), které můžete použít k nasazení specifických knihoven a které zahrnete do souboru Instalační služba systému Windows aplikace (. msi).

Distribuovatelný soubor balíčku nainstaluje všechny knihovny vizuálů C++ pro konkrétní architekturu systému. Například pokud je vaše aplikace sestavena pro x64, můžete použít Distribuovatelný balíček VCRedist_x64. exe k instalaci všech knihoven vizuálů C++ , které vaše aplikace používá. Před instalací aplikace můžete instalačnímu programu aplikace spustit Distribuovatelný balíček jako požadavek.

Slučovací modul umožňuje zahrnutí logiky nastavení pro konkrétní vizuální C++ knihovnu do instalačního souboru aplikace Instalační služba systému Windows. V případě, že vaše aplikace vyžaduje, můžete zahrnout libovolný počet slučovacích modulů. Slučovací moduly použijte, pokud potřebujete minimalizovat velikost binárních souborů nasazení.

Vzhledem k tomu, že centrální nasazení pomocí redistribuovatelného balíčku nebo slučovacích modulů umožňuje web Windows Update automatickou aktualizaci C++ knihoven vizuálů, doporučujeme použít knihovny DLL knihoven v aplikaci místo statických knihoven a použít centrální nasazení místo místního nasazení.

## <a name="local-deployment"></a>Místní nasazení

V místním nasazení jsou soubory knihoven nainstalovány ve složce aplikace společně se spustitelným souborem. Do stejné složky lze C++ nainstalovat různé verze Visual redistribuovatelných knihoven, protože název souboru každé verze zahrnuje číslo jeho verze. Například verze 12 C++ běhové knihovny je msvcp120. dll a verze 14 je msvcp140. dll.

Knihovna může být rozdělena mezi více dalších knihoven DLL, označovaných jako *knihovny teček*. Například některé funkce ve standardní knihovně vydané v aplikaci Visual Studio 2017 verze 15,6 byly přidány do souboru msvcp140_1. dll pro zachování kompatibility ABI msvcp140. dll. Pokud používáte sadu Visual Studio 2017 verze 15,6 (sada nástrojů 14,13) nebo novější sadu nástrojů ze sady Visual Studio 2017, možná budete muset tyto knihovny teček nasadit místně i do hlavní knihovny. Tyto samostatné knihovny teček jsou následně zahrnuty do další hlavní verze základní knihovny, když se ABI změní.

Vzhledem k tomu, že společnost Microsoft nemůže C++ automaticky aktualizovat místně nasazené vizuální knihovny, nedoporučujeme místní nasazení těchto knihoven. Pokud se rozhodnete použít místní nasazení distribuovatelných knihoven, doporučujeme implementovat vlastní metodu automatických aktualizací místně nasazených knihoven.

## <a name="static-linking"></a>Statické propojení

Kromě dynamicky propojených knihoven aplikace Visual Studio poskytuje většinu svých knihoven jako statické knihovny. Statickou knihovnu je možné staticky propojit s vaší aplikací, to znamená propojit kód objektu knihovny přímo do aplikace. Tím se vytvoří jeden binární soubor bez závislosti DLL, takže nemusíte nasazovat soubory knihovny vizuálů C++ samostatně. Tento přístup však nedoporučujeme, protože staticky propojené knihovny nelze aktualizovat na místě. Pokud používáte statické propojení a potřebujete propojené knihovny aktualizovat, je nutné aplikaci znovu zkompilovat a opětovně nasadit.

## <a name="troubleshooting-deployment-issues"></a>Řešení potíží s nasazením

Pořadí načítání vizuálních C++ knihoven je závislé na systému. Chcete-li diagnostikovat problémy zavaděče, použijte nástroj depends.exe nebo where.exe. Další informace naleznete v tématu [pořadí hledání dynamické knihovny (Windows)](/windows/win32/Dlls/dynamic-link-library-search-order).

## <a name="see-also"></a>Viz také:

- [Nasazení desktopových aplikací](deploying-native-desktop-applications-visual-cpp.md)
- [Univerzální nasazení CRT](universal-crt-deployment.md)
