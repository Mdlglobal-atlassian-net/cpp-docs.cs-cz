---
title: Universal CRT nasazení | Microsoft Docs
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
ms.openlocfilehash: 20006118d4bf27c379b78b84dc8807a4fd6c5e6c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34256314"
---
# <a name="universal-crt-deployment"></a>Nasazení Universal CRT

Ze sady Visual Studio .NET pomocí Visual Studio 2013 má každý hlavní verzi nástroje a kompilátor C++ zahrnuty nové, samostatnou verzi knihovny Microsoft C Runtime (CRT). Tyto samostatné verze CRT nebyly nezávisle z a do různých stupňů, vzájemně kompatibilní. Například knihovnou CRT používanou v sadě Visual Studio 2012 byla verze 11, s názvem msvcr110.dll a CRT používá Visual Studio 2013 byl verze 12, s názvem msvcr120.dll. Od verze sady Visual Studio 2015, to už tento případ. Visual Studio 2015 a novější verze sady Visual Studio všechny použijte jeden Universal CRT.

Universal CRT je součástí operačního systému Microsoft Windows. Je součástí operačního systému ve Windows 10 a je k dispozici pro starší operační systémy Windows Vista prostřednictvím Windows 8.1 pomocí služby Windows Update. Kromě toho místní nasazení Universal CRT je podporováno, s určitými omezeními.

## <a name="central-deployment"></a>Centrální nasazení

Preferovaná metoda centrálně nainstalovat Universal CRT je systém Microsoft Windows Update. Universal CRT je že doporučené aktualizace pro všechny podporované operační systémy Microsoft Windows, tak, že výchozí, většina počítačů ji nainstalovat jako součást procesu pravidelné aktualizace. Počáteční verze Universal CRT byl [KB2999226](https://support.microsoft.com/en-us/kb/2999226); následné aktualizace s různými opravami chyb byl proveden v [KB3118401](https://support.microsoft.com/en-us/kb/3118401), a byly další aktualizace s další oprav chyb a nové funkce. Novější aktualizace hledání [support.microsoft.com](https://support.microsoft.com) pro univerzální C Runtime nebo Universal CRT.

Ne všechny počítače s Microsoft Windows pravidelně nainstalujte aktualizace pomocí služby Windows Update a některé nemusí nainstalovat všechny doporučené aktualizace. Pro podporu použití aplikace vytvořené pomocí sady Visual Studio 2015 a novější modulové C++ na těch počítačů, nejsou Universal CRT redistributables k dispozici pro distribuci do režimu offline. Tyto redistributables může stáhnout z jedné z výše uvedených KB odkazy. Upozorňujeme, že redistributables Universal CRT vyžadovat, že tento počítač byl aktualizován na aktuální aktualizaci service Pack. Ano například redistributable pro systém Windows 7 je možné instalovat pouze na systém Windows 7 SP1, není Windows 7 RTM.

Protože základní závislostí knihoven C++ Universal CRT se nainstaluje Visual C++ redistributable (VCRedist) základní verzi Universal CRT na počítačích, které nemají verze již nainstalované, dostatečná pro uspokojení knihovna C++ závislosti. Pokud je aplikace závislá na novější verzi Universal CRT, je nutné nainstalovat tento novější verzi explicitně. Doporučujeme nainstalovat před instalací VCRedist, aby se zabránilo potenciální více vyžaduje restartování počítače.

## <a name="local-deployment"></a>Místní nasazení

Místní nasazení Universal CRT je podporováno, ale nedoporučuje se z důvodů zabezpečení a výkonu.  Knihovny DLL pro místní nasazení jsou zahrnuty jako součást sady Windows SDK v sadách Windows\\10\\Redist\\ucrt\\podadresáři knihovny DLL, podle počítače architektury. Knihovny DLL vyžaduje ucrtbase.dll a sadu APISet předávání s názvem rozhraní api knihovny DLL-ms-win -\*.dll. Sada knihoven DLL potřeba na každý operační systém se liší, proto se důrazně doporučuje, zahrnete všechny knihovny DLL při nasazování místně.

Existují dvě omezení na místní nasazení zajímat:

- Ve Windows 10 Universal CRT v adresáři systému se používá vždycky, i když aplikace obsahuje kopii Universal CRT místní aplikace. To platí i v případě, že místní kopii Universal CRT je novější. Je to proto Universal CRT je základní součástí operačního systému na Windows 10.

- Ve verzích systému Windows než Windows 8 nelze Universal CRT místně zabalené pomocí modulu plug-in, který je umístěný v adresáři než adresář, který obsahuje hlavní spustitelný soubor pro vaši aplikaci. Nelze přeložit ucrtbase.dll úspěšně v tomto případě jsou předávání APISet knihovny DLL. Některé doporučené alternativní řešení patří:

  - Statické propojení Universal CRT
  - Centrální nasazení Universal CRT nebo
  - Soubory Universal CRT umístíte ve stejném adresáři jako aplikace.

## <a name="deployment-on-microsoft-windows-xp"></a>Nasazení systému Microsoft Windows XP

Visual Studio 2015 a Visual Studio 2017 nadále podporují vývoj softwaru pro použití v systému Microsoft Windows XP. Za tímto účelem verzi Universal CRT funguje v systému Microsoft Windows XP. Operační systém Microsoft Windows XP je již v všeobecně nebo rozšířenou podporu, takže centrální nasazení Universal CRT na Microsoft Windows XP se liší od jiných operačních systémech.

Když Visual C++ redistributable je nainstalovaný na Windows XP, přímo nainstaluje Universal CRT a všechny jeho závislosti do systémového adresáře, bez instalace nebo v závislosti na žádné služby Windows Update. Redistributable slučovacích modulů, Microsoft_VC*verze*_CRT_\*soubory .msm totéž.

Místní nasazení Universal CRT na systému Windows XP je stejné jako u ostatních podporovaných operačních systémů.

## <a name="see-also"></a>Viz také:

- [Nasazení ve Visual C++](deployment-in-visual-cpp.md)
