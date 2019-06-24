---
title: Univerzální nasazení CRT
ms.date: 05/11/2018
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
ms.openlocfilehash: 1f6e685cca65c4b31ac2e6147341c4b5a3fe8228
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344462"
---
# <a name="universal-crt-deployment"></a>Univerzální nasazení CRT

Ze sady Visual Studio .NET pomocí Visual Studio 2013 má každá hlavní verze kompilátoru jazyka C++ a nástroje zahrnuté novou samostatnou verzi knihovny Microsoft C Runtime (CRT). Tyto samostatné verze CRT byly nezávisle z a na různých úrovních, vzájemně nekompatibilní. Například CRT knihovny používají Visual Studio 2012 se verze 11, pojmenované msvcr110.dll a CRT používá Visual Studio 2013 se verze 12, pojmenované msvcr120.dll. Od v sadě Visual Studio 2015, už nejsou případu. Visual Studio 2015 a novější verze sady Visual Studio všechny použít jeden Universal CRT.

Universal CRT je součástí operačního systému Microsoft Windows jsou součástí operačního systému ve Windows 10. Je dostupná pro starší operační systémy Windows Vista až Windows 8.1 pomocí služby Windows Update. Místní nasazení Universal CRT je podporován, s určitými omezeními.

## <a name="central-deployment"></a>Centrální nasazení

Upřednostňuje se centrálně nainstalovat komponentu Universal CRT je používání služby Microsoft Windows Update. Universal CRT je že doporučené aktualizace pro všechny podporované operační systémy Microsoft Windows, tak, že výchozí, většina počítačů ji nainstalovat jako součást procesu pravidelné aktualizace. Počáteční verze na Universal CRT byla [KB2999226](https://support.microsoft.com/kb/2999226). Byla vytvořena novější aktualizace s různé opravy chyb v [KB3118401](https://support.microsoft.com/kb/3118401), a aby byla další aktualizace s další opravy chyb a nové funkce. Novější aktualizace hledání [support.microsoft.com](https://support.microsoft.com) Universal C Runtime nebo Universal CRT.

Ne všechny počítače Windows Microsoft pravidelně instalace aktualizací pomocí Windows Update, a některé nemusí nainstalovat všechny doporučené aktualizace. Pro podporu používání aplikace sestavené pomocí sady Visual Studio 2015 a novější C++ sady nástrojů na těchto počítačích nejsou k dispozici pro offline distribuci Universal CRT redistribuovatelné soubory. Tyto distribuovatelné soubory stáhnout z jednoho z uvedených odkazů KB. Distribuovatelné součásti Universal CRT vyžaduje, že je počítač se aktualizovala na aktuální aktualizaci service pack. Ano například distribuovatelné součásti pro Windows 7 je možné instalovat pouze do Windows 7 SP1, ne Windows 7 RTM.

Protože Universal CRT je základní závislost C++ knihovny, vizuál C++ redistributable (VCRedist) nainstaluje na počítače, které již nemáte nainstalován počáteční verzi sady Universal CRT (verze 10.0.10240). Tato verze je dostatečná pro uspokojení C++ závislé položky knihoven. Pokud je aplikace závislá na novější verzi Universal CRT, musíte používání plně aktuálním stavu počítače pomocí služby Windows Update nebo explicitně nainstalovat tuto verzi. Doporučujeme nainstalovat modul Universal C Runtime prostřednictvím Windows Update nebo MSU před instalací VCRedist, aby se zabránilo potenciální více vyžaduje restartování.

Všechny operační systémy mají nárok nejnovější modul Universal C Runtime prostřednictvím služby Windows Update. Ve Windows 10 centrálně nasazené verze odpovídá verzi operačního systému. K aktualizaci Universal C Runtime dál, je nutné aktualizovat operační systém. Pro Windows Vista až Windows 8.1 je nejnovější dostupný Universal C Runtime aktuálně podle verze zahrnuté ve Windows 10 Anniversary Update (verze 10.0.14393) další opravy.

## <a name="local-deployment"></a>Místní nasazení

Místní nasazení Universal CRT je podporován, ale nedoporučuje se z důvodů zabezpečení a výkonu. Knihovny DLL pro místní nasazení jsou zahrnuty jako součást sady Windows SDK v sady Windows\\10\\Redist\\ucrt\\podadresář knihovny DLL pomocí architektury počítače. Knihovny DLL vyžaduje ucrtbase.dll a sadu APISet předávání knihovny DLL s názvem rozhraní api-ms-Windows -\*.dll. Sadu knihoven DLL vyžaduje na všech operačních systémech se liší. Důrazně doporučujeme, že zahrnete všechny knihovny DLL místní nasazení.

Existují dvě omezení na místní nasazení je potřeba vědět:

- Ve Windows 10 komponentu Universal CRT v adresáři systému se používá vždycky, i v případě, že aplikace obsahuje aplikaci místní kopii Universal CRT. To platí i v případě, že je místní kopii novější, protože Universal CRT je základní součástí operačního systému na Windows 10.

- Ve verzích Windows než Windows 8 komponentu Universal CRT nejde zabalit, místně pomocí modulu plug-in, pokud je umístěn v adresáři než directory hlavní spustitelný soubor aplikace. Nelze přeložit ucrtbase.dll úspěšně v tomto případě jsou předávání APISet knihovny DLL. Zahrnout některé doporučená alternativní řešení:

  - Staticky propojit Universal CRT
  - Centrálně nasadit na Universal CRT, nebo
  - Soubory Universal CRT umístíte ve stejném adresáři jako aplikace.

## <a name="deployment-on-microsoft-windows-xp"></a>Nasazení v Microsoft Windows XP

Visual Studio 2015 a Visual Studio 2017 se nadále podporovat vývoje softwaru pro použití v systému Microsoft Windows XP. Pro podporu této vývoje aplikací, verzi Universal CRT funguje v systému Microsoft Windows XP. Operační systém Microsoft Windows XP už je v hlavní fáze technické nebo rozšířenou podporu centrální nasazení do systému Microsoft Windows XP na Universal CRT se liší od jiných operačních systémech.

Když vizuál C++ redistributable je nainstalovaný na Windows XP, přímo se nainstaluje na Universal CRT a všechny jeho závislosti do systémového adresáře. Nepodporuje instalaci nebo závisí na všechny aktualizace Windows. Distribuovatelné slučovací moduly Microsoft_VC*verze*_CRT_\*soubory .msm totéž.

Místní nasazení Universal CRT na Windows XP je stejný jako v ostatních podporovaných operačních systémů.

## <a name="see-also"></a>Viz také:

- [Nasazení ve Visual C++](deployment-in-visual-cpp.md)
