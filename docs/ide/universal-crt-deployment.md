---
title: Nasazení Universal CRT | Dokumentace Microsoftu
ms.custom: ''
ms.date: 05/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7fe21753dc4310752c1081d17ddff942bcbd89f
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820994"
---
# <a name="universal-crt-deployment"></a>Nasazení Universal CRT

Ze sady Visual Studio .NET pomocí Visual Studio 2013 má každá hlavní verze kompilátoru jazyka C++ a nástroje zahrnuté novou samostatnou verzi knihovny Microsoft C Runtime (CRT). Tyto samostatné verze CRT byly nezávisle z a na různých úrovních, vzájemně nekompatibilní. Například CRT knihovny používají Visual Studio 2012 se verze 11, pojmenované msvcr110.dll a CRT používá Visual Studio 2013 se verze 12, pojmenované msvcr120.dll. Od v sadě Visual Studio 2015, to je už tento případ. Visual Studio 2015 a novější verze sady Visual Studio všechny použít jeden Universal CRT.

Universal CRT je součástí operačního systému Microsoft Windows. Je součástí operačního systému ve Windows 10 a je k dispozici pro starší operační systémy Windows Vista až Windows 8.1 pomocí služby Windows Update. Kromě toho místní nasazení Universal CRT je podporován, s určitými omezeními.

## <a name="central-deployment"></a>Centrální nasazení

Upřednostňuje se centrálně nainstalovat komponentu Universal CRT je používání služby Microsoft Windows Update. Universal CRT je že doporučené aktualizace pro všechny podporované operační systémy Microsoft Windows, tak, že výchozí, většina počítačů ji nainstalovat jako součást procesu pravidelné aktualizace. Byl původní verzi Universal CRT [KB2999226](https://support.microsoft.com/kb/2999226); byl proveden následné aktualizace s různé opravy chyb v [KB3118401](https://support.microsoft.com/kb/3118401), a aby byla další aktualizace s další opravy chyb a nové funkce. Novější aktualizace hledání [support.microsoft.com](https://support.microsoft.com) Universal C Runtime nebo Universal CRT.

Ne všechny počítače Windows Microsoft pravidelně instalace aktualizací pomocí Windows Update, a některé nemusí nainstalovat všechny doporučené aktualizace. Pro podporu použití aplikace vytvořené pomocí sady Visual Studio 2015 a novější sady nástrojů C++ na těchto počítačích, k dispozici redistribuovatelnost Universal CRT pro distribuci v režimu offline. Tyto distribuovatelné součásti stáhnout z jednoho z uvedených odkazů KB. Všimněte si, že redistribuovatelnost Universal CRT vyžadovat, že je počítač se aktualizovala na aktuální aktualizaci service pack. Ano například distribuovatelné součásti pro Windows 7 je možné instalovat pouze do Windows 7 SP1, ne Windows 7 RTM.

Protože Universal CRT je základní závislostí knihoven C++, jazyce Visual C++ redistributable (VCRedist) nainstaluje základní verzi Universal CRT na počítačích, které nemají verze již nainstalovaný, dostatečná pro uspokojení knihovny C++ závislosti. Pokud je aplikace závislá na novější verzi Universal CRT, je nutné explicitně nainstalovat této novější verzi. Doporučujeme nainstalovat před instalací VCRedist, aby se zabránilo potenciální více vyžaduje restartování.

## <a name="local-deployment"></a>Místní nasazení

Místní nasazení Universal CRT je podporován, ale nedoporučuje se z důvodů zabezpečení a výkonu.  Knihovny DLL pro místní nasazení jsou zahrnuty jako součást sady Windows SDK v sady Windows\\10\\Redist\\ucrt\\podadresář knihovny DLL pomocí architektury počítače. Knihovny DLL vyžaduje ucrtbase.dll a sadu APISet předávání knihovny DLL s názvem rozhraní api-ms-Windows -\*.dll. Sadu knihoven DLL vyžaduje na všech operačních systémech liší, proto důrazně doporučujeme, že zahrnete všechny knihovny DLL místní nasazení.

Existují dvě omezení na místní nasazení je potřeba vědět:

- Ve Windows 10 komponentu Universal CRT v adresáři systému se používá vždycky, i v případě, že aplikace obsahuje aplikaci místní kopii Universal CRT. To platí i v případě, že místní kopie Universal CRT je novější. Je to proto Universal CRT je základní součástí operačního systému na Windows 10.

- Ve verzích Windows než Windows 8 komponentu Universal CRT nejde zabalit, místně pomocí modulu plug-in, který se nachází v na jiný adresář než adresář, který obsahuje hlavní spustitelný soubor pro vaši aplikaci. Nelze přeložit ucrtbase.dll úspěšně v tomto případě jsou předávání APISet knihovny DLL. Zahrnout některé doporučená alternativní řešení:

  - Staticky propojit Universal CRT
  - Centrálně nasadit na Universal CRT, nebo
  - Soubory Universal CRT umístíte ve stejném adresáři jako aplikace.

## <a name="deployment-on-microsoft-windows-xp"></a>Nasazení v Microsoft Windows XP

Visual Studio 2015 a Visual Studio 2017 se nadále podporovat vývoje softwaru pro použití v systému Microsoft Windows XP. Pro podporu této verze Universal CRT funguje v systému Microsoft Windows XP. Operační systém Microsoft Windows XP už je v hlavní fáze technické nebo rozšířenou podporu centrální nasazení do systému Microsoft Windows XP na Universal CRT se liší od jiných operačních systémech.

Když Visual C++ redistributable je nainstalovaný na Windows XP, přímo nainstaluje Universal CRT a všechny jeho závislosti do systémového adresáře, bez nutnosti instalace nebo v závislosti na všechny aktualizace Windows. Distribuovatelné slučovací moduly Microsoft_VC*verze*_CRT_\*soubory .msm totéž.

Místní nasazení Universal CRT na Windows XP je stejný jako v ostatních podporovaných operačních systémů.

## <a name="see-also"></a>Viz také:

- [Nasazení ve Visual C++](deployment-in-visual-cpp.md)
