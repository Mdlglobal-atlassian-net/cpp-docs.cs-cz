---
title: Sestavení souběžných sestavení C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: 6e49ba72a397efb97437a2f7e6d721c782875c48
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493330"
---
# <a name="building-cc-side-by-side-assemblies"></a>Sestavení souběžných sestavení C/C++

[Souběžné sestavení](/windows/win32/SbsCs/about-side-by-side-assemblies-) je kolekce prostředků – skupina knihoven DLL, třídy systému Windows, servery com, knihovny typů nebo rozhraní, které jsou k dispozici pro aplikaci pro použití za běhu. Hlavní výhodou opětovného sbalení knihoven DLL v sestavení je, že aplikace současně může používat více verzí sestavení a je možné v případě vydání aktualizace Service aktuálně nainstalovaná sestavení použít.

Aplikace C++ může použít jednu nebo několik knihoven DLL v různých částech aplikace. V době běhu jsou knihovny DLL načteny do hlavního procesu a je proveden požadovaný kód. Aplikace spoléhá na to, že operační systém najde požadované knihovny DLL, zjistíte, jaké další závislé knihovny DLL musí být načteny a poté je nahraje společně s požadovanou knihovnou DLL. V operačních systémech Windows starších než Windows XP, Windows Server 2003 a Windows Vista vyhledává zavaděč operačního systému závislé knihovny DLL buď v místní složce aplikace, nebo v jiné složce určené v systémové cestě. V systémech Windows XP, Windows Server 2003 a Windows Vista může zavaděč operačního systému také vyhledat závislé knihovny DLL pomocí souboru [manifestu](/windows/win32/sbscs/manifests) a vyhledat souběžná sestavení, která obsahují tyto knihovny DLL.

Ve výchozím nastavení platí, že když je knihovna DLL sestavena se sadou Visual Studio, má [manifest aplikace](/windows/win32/SbsCs/application-manifests) vložený jako prostředek RT_MANIFEST s ID se rovná 2. Stejně jako u spustitelného souboru tento manifest popisuje závislosti této knihovny DLL v jiných sestaveních. To předpokládá, že knihovna DLL není součástí souběžného sestavení a aplikace, které závisí na této knihovně DLL, nepoužívají k načtení manifest aplikace, ale místo toho využívají zavaděč operačního systému k nalezení této knihovny DLL v systémové cestě.

> [!NOTE]
> Pro knihovnu DLL, která používá manifest aplikace, je důležité, aby byl manifest vložen jako prostředek s ID rovno 2. Pokud je knihovna DLL dynamicky načtena za běhu (například pomocí funkce [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) ), zavaděč operačního systému načte závislá sestavení zadaná v manifestu knihovny DLL. Manifest externí aplikace pro knihovny DLL není kontrolován během `LoadLibrary` volání. Pokud není manifest vložen, zavaděč se může pokusit načíst nesprávné verze sestavení nebo najít závislá sestavení, která se nepodařilo najít.

Jednu nebo několik souvisejících knihoven DLL lze znovu zabalit do souběžného sestavení s odpovídajícím [manifestem sestavení](/windows/win32/SbsCs/assembly-manifests), který popisuje, které soubory tvoří sestavení a také závislost sestavení v jiných souběžných sestaveních.

> [!NOTE]
> Pokud sestavení obsahuje jednu knihovnu DLL, doporučuje se vložit manifest sestavení do této knihovny DLL jako prostředek s ID, který je roven 1, a dát soukromému sestavení stejný název jako knihovna DLL. Například pokud je název knihovny DLL MyLibrary. dll, hodnota atributu name použitá v prvku \<assemblyIdentity> manifestu může být také MyLibrary. V některých případech, pokud má knihovna jinou příponu než. dll (například projekt ovládacích prvků MFC ActiveX vytvoří knihovnu. ocx), lze vytvořit manifest externího sestavení. V tomto případě musí být název sestavení a jeho manifestu jiný než název knihovny DLL (například MyAssembly, MyAssembly. manifest a MyLibrary. ocx). Přesto se však doporučuje tyto knihovny přejmenovat tak, aby měly příponu. dll, a vložit manifest jako prostředek, aby se snížily budoucí náklady na údržbu tohoto sestavení. Další informace o tom, jak operační systém hledá soukromá sestavení, naleznete v tématu [pořadí vyhledávání sestavení](/windows/win32/SbsCs/assembly-searching-sequence).

Tato změna může umožňovat nasazení odpovídajících knihoven DLL jako [privátní sestavení](/windows/win32/Msi/private-assemblies) v místní složce aplikace nebo jako [sdílené sestavení](/windows/win32/Msi/shared-assemblies) v mezipaměti sestavení WinSxS. Je nutné provést několik kroků, aby bylo možné dosáhnout správného běhového chování tohoto nového sestavení; jsou popsány v [tématu pokyny pro vytváření souběžných sestavení](/windows/win32/SbsCs/guidelines-for-creating-side-by-side-assemblies). Jakmile je sestavení správně vytvořeno, může být nasazeno jako sdílené nebo privátní sestavení společně s aplikací, která na něm závisí. Při instalaci souběžných sestavení jako sdíleného sestavení můžete postupovat podle pokynů uvedených v části [instalace Win32 sestavení pro souběžné sdílení v systému Windows XP](/windows/win32/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp) nebo použití [slučovacích modulů](/windows/win32/msi/merge-modules). Při instalaci souběžných sestavení jako privátního sestavení můžete pouze zkopírovat odpovídající knihovnu DLL, prostředky a manifest sestavení jako součást procesu instalace do místní složky aplikace v cílovém počítači. Zajistěte, aby bylo toto sestavení nalezeno zavaděčem za běhu (viz [sekvence vyhledávání sestavení](/windows/win32/SbsCs/assembly-searching-sequence)). Další možností je použít [Instalační služba systému Windows](/windows/win32/Msi/windows-installer-portal) a postupovat podle pokynů uvedených v části [instalace Win32 sestavení pro soukromé použití aplikace v systému Windows XP](/windows/win32/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp).

## <a name="see-also"></a>Viz také

[Sestavení izolovaných aplikací C/C++](building-c-cpp-isolated-applications.md)<br/>
[Sestavení izolovaných aplikací C/C++ a souběžných sestavení](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
