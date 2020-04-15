---
title: Nasazení ve Visual C++
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
ms.openlocfilehash: 5c4b75a65fcfb34a4988b176ffcb5b2afcb7ea13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377376"
---
# <a name="deployment-in-visual-c"></a>Nasazení ve Visual C++

Instalace aplikace do jiného počítače, než je vývojový počítač, se označuje jako *nasazení*. Při nasazení aplikace Visual C++ do jiného počítače je nutné nainstalovat aplikaci i všechny soubory knihovny, na kterých závisí. Visual Studio umožňuje tři způsoby nasazení knihoven Visual C++ společně s vaší aplikací: *centrální nasazení*, *místní nasazení*a statické *propojení*. Centrální nasazení umístí soubory knihovny pod adresář systému Windows, kde je služba Windows Update může automaticky aktualizovat. Místní nasazení umístí soubory knihovny do stejného adresáře jako vaše aplikace. Je nutné znovu nasadit všechny místně nasazené knihovny sami, abyste je aktualizovali. Statické propojení sváže kód knihovny do aplikace. Je nutné znovu zkompilovat a znovu nasadit aplikaci využít všechny aktualizace knihoven při použití statické propojení.

V sadě Visual Studio 2015 byla knihovna Microsoft C Runtime refaktorována na komponenty místní knihovny specifické pro verzi a novou knihovnu Universal C Runtime, která je nyní součástí systému Windows. Podrobnosti o nasazení univerzální crt, naleznete [v tématu univerzální CRT nasazení](universal-crt-deployment.md).

## <a name="central-deployment"></a>Centrální nasazení

V centrálním nasazení jsou soubory knihovny DLL nainstalovány v adresáři Windows\System32 nebo pro 32bitové soubory knihovny v systémech x64 v adresáři Windows\SysWow64. Společnost Microsoft automaticky aktualizuje knihovny, které jsou nasazeny centrálně. Pro knihovny Visual C++, které jsou místně nasazené nebo staticky propojené, musíte poskytnout aktualizace.

Chcete-li centrálně nasadit knihovny Visual C++, můžete pro instalaci souborů použít jeden z těchto dvou zdrojů:

- *Redistribuovatelné* soubory balíčků, což jsou samostatné spustitelné soubory příkazového řádku, které obsahují všechny redistribuovatelné knihovny Visual C++ v komprimované podobě, nebo

- *Redistribuovatelné slučovací moduly* (soubory msm), které můžete použít k nasazení konkrétních knihoven a které zahrnete do souboru Instalační služby systému Windows (.msi) vaší aplikace.

Redistribuovatelný soubor balíčku nainstaluje všechny knihovny Visual C++ pro konkrétní architekturu systému. Pokud je například vaše aplikace vytvořena pro x64, můžete použít redistribuovatelný balíček vcredist_x64.exe k instalaci všech knihoven Visual C++, které vaše aplikace používá. Instalační program aplikace můžete naprogramovat tak, aby před instalací aplikace spouštěl redistribuovatelný balíček jako předpoklad.

Slučovací modul umožňuje zahrnout logiku nastavení pro konkrétní knihovnu Visual C++ do instalačního souboru instalační aplikace Instalační služby systému Windows. Můžete zahrnout tolik nebo tolik slučovacích modulů, kolik vaše aplikace vyžaduje. Slučovací moduly použijte v případě, že potřebujete minimalizovat velikost binárních souborů nasazení.

Vzhledem k tomu, že centrální nasazení pomocí redistribuovatelného balíčku nebo slučovacích modulů umožňuje službě Windows Update automaticky aktualizovat knihovny Visual C++, doporučujeme použít knihovny DLL ve vaší aplikaci namísto statických knihoven a použít centrální nasazení namísto místního nasazení.

## <a name="local-deployment"></a>Místní nasazení

V místním nasazení jsou soubory knihovny nainstalovány ve složce aplikace spolu s spustitelným souborem. Různé verze knihoven Visual C++ redistribuovatelné lze nainstalovat do stejné složky, protože název souboru každé verze obsahuje číslo verze. Například verze 12 knihovny runtime jazyka C++ je msvcp120.dll a verze 14 je msvcp140.dll.

Knihovna může být rozložena mezi více dalších knihoven DLL, označovaných jako *knihovny dot*. Například některé funkce ve standardní knihovně vydané ve Visual Studiu 2017 verze 15.6 byla přidána do msvcp140_1.dll zachovat kompatibilitu ABI msvcp140.dll. Pokud používáte Visual Studio 2017 verze 15.6 (sada nástrojů 14.13) nebo novější sadu nástrojů z Visual Studia 2017, budete pravděpodobně muset místně nasadit tyto knihovny temenek, stejně jako hlavní knihovny. Tyto samostatné tečkové knihovny jsou pak vráceny do další hlavní verze základní knihovny při změně ABI.

Vzhledem k tomu, že společnost Microsoft nemůže automaticky aktualizovat místně nasazené knihovny Visual C++, nedoporučujeme místní nasazení těchto knihoven. Pokud se rozhodnete použít místní nasazení distribuovatelných knihoven, doporučujeme implementovat vlastní metodu automatických aktualizací místně nasazených knihoven.

## <a name="static-linking"></a>Statické propojení

Kromě dynamicky propojených knihoven poskytuje Visual Studio většinu svých knihoven jako statické knihovny. Staticky můžete staticky propojit statickou knihovnu s vaší aplikací, to znamená propojit objektový kód knihovny přímo do aplikace. Tím se vytvoří jeden binární soubor bez závislosti knihovny DLL, takže není třeba nasadit soubory knihovny Visual C++ samostatně. Tento přístup však nedoporučujeme, protože staticky propojené knihovny nelze aktualizovat na místě. Pokud používáte statické propojení a potřebujete propojené knihovny aktualizovat, je nutné aplikaci znovu zkompilovat a opětovně nasadit.

## <a name="troubleshooting-deployment-issues"></a>Poradce při potížích s nasazením

Pořadí načítání knihoven Visual C++ je závislé na systému. Chcete-li diagnostikovat problémy zavaděče, použijte nástroj depends.exe nebo where.exe. Další informace naleznete v [tématu Dynamic-Link Library Search Order (Windows)](/windows/win32/Dlls/dynamic-link-library-search-order).

## <a name="see-also"></a>Viz také

- [Nasazení desktopových aplikací](deploying-native-desktop-applications-visual-cpp.md)
- [Univerzální nasazení CRT](universal-crt-deployment.md)
