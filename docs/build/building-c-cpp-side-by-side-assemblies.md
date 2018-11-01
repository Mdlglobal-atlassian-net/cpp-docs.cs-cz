---
title: Sestavení souběžných sestavení C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: cf3fb532e70e047938b9a575eefdcceadceeceda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476307"
---
# <a name="building-cc-side-by-side-assemblies"></a>Sestavení souběžných sestavení C/C++

A [sestavení vedle sebe](/windows/desktop/SbsCs/about-side-by-side-assemblies-) je kolekce prostředků – Skupina knihoven DLL, třídy systému windows, serverů COM, knihoven typů nebo rozhraní – k dispozici pro aplikaci pro použití za běhu. Hlavní výhodou opakovanému balení knihovny DLL v sestavení je, že aplikace může používat více verzí sestavení ve stejnou dobu a je možné aktuálně nainstalovanou službu sestavení v případě vydání verze update.

Aplikace v jazyce Visual C++ může používat jednu nebo několik knihoven DLL v různých částí aplikace. Za běhu knihovny DLL se načtou do hlavní proces a je proveden požadovaný kód. Aplikace závisí na operačním systému najít požadované knihovny DLL, pochopit, jaké dalších závislých knihoven DLL mají načíst a pak je načíst spolu s požadovanou knihovnu DLL. Ve verzích operačních systémů Windows starších než Windows XP, Windows Server 2003 a Windows Vista na zavaděči operačního systému hledá závislé knihovny DLL v místní složce aplikace nebo jiné složky zadané v systémové cestě. Na Windows XP, Windows Server 2003 a Windows Vista na zavaděči operačního systému můžete také vyhledat pomocí závislých knihoven DLL [manifest](https://msdn.microsoft.com/library/windows/desktop/aa375365) soubor a vyhledejte sestavení vedle sebe, které obsahují tyto knihovny DLL.

Ve výchozím nastavení, při vytváření knihovny DLL pomocí sady Visual Studio, má [manifest aplikace](/windows/desktop/SbsCs/application-manifests) vložený jako prostředek RT_MANIFEST s ID roven 2. Stejně jako u spustitelný soubor tento manifest popisuje závislosti této knihovny DLL na jiná sestavení. Předpokladem je, že knihovna DLL není součástí sestavení vedle sebe a aplikace, které závisí na tuto knihovnu DLL nebudou používat manifest aplikace načíst, ale místo toho spoléhají na zavaděči operačního systému k vyhledání této knihovny DLL v systémové cestě.

> [!NOTE]
> Je důležité pro knihovnu DLL, která používá manifest aplikace má manifest vložený jako prostředek s ID roven 2. Pokud načtení knihovny DLL dynamicky za běhu (například pomocí [voláním LoadLibrary vloženým pomocí](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya) funkce), operační systém načte závislá sestavení určená v manifestu knihovny DLL. Manifest externí aplikace pro knihovny DLL není kontrolován během `LoadLibrary` volání. Pokud v manifestu není vložená, zavaděč může opakovat pokus o načtení nesprávné verze sestavení, nebo se nedaří najít k hledání závislých sestavení.

Jeden nebo několik týkající se knihoven DLL může být znovu zabalené, sadu do sestavení vedle sebe s odpovídající [manifestu sestavení](/windows/desktop/SbsCs/assembly-manifests), která popisuje soubory, které tvoří sestavení, jakož i závislost sestavení na jiné side-by-side sestavení.

> [!NOTE]
> Pokud sestavení obsahuje jednu knihovnu DLL, se doporučuje pro vložení manifestu sestavení do této knihovny DLL jako prostředek s ID je rovno 1 a poskytněte soukromé sestavení se stejným názvem jako knihovnu DLL. Například pokud je název knihovny DLL mylibrary.dll, hodnotu atributu název se používá v \<assemblyIdentity > Moje knihovna je také možné elementu v manifestu. V některých případech, když má příponou jinou než DLL knihovny (například projekt aplikace knihovny MFC – ovládací prvky ActiveX vytvoří knihovnu .ocx) je možné vytvořit manifest externí sestavení. V tomto případě název sestavení a jeho manifestu musí být jiný než název knihovny DLL (například MyAssembly, MyAssembly.manifest a mylibrary.ocx). Ale stále doporučujeme přejmenovat tyto knihovny, které chcete mít extension.dll a vložit do manifestu jako prostředek snížit náklady na budoucí údržbu tohoto sestavení. Další informace o způsobu soukromých sestavení hledá operační systém, najdete v části [pořadí hledání sestavení](/windows/desktop/SbsCs/assembly-searching-sequence).

Tato změna může povolit nasazení odpovídající knihovny DLL jako [soukromé sestavení](/windows/desktop/Msi/private-assemblies) do místní složky aplikace nebo jako [sdílené sestavení](/windows/desktop/Msi/shared-assemblies) WinSxS mezipaměti sestavení. Několik kroků musí následovat, abyste dosáhli správný modul runtime chování tohoto nového sestavení; Tyto toky jsou popsané v [pokyny pro vytváření sestavení vedle sebe](/windows/desktop/SbsCs/guidelines-for-creating-side-by-side-assemblies). Po sestavení je správně vytvořený můžete nasadit jako buď sdílené nebo soukromé sestavení společně s aplikací, které na ní závisí. Při instalaci sestavení vedle sebe jako sdílená sestavení, můžete buď postupujte podle pokynů uvedených v [instalaci sestavení Win32 pro sdílení vedle sebe na Windows XP](/windows/desktop/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp) nebo použijte [slučovací moduly](https://msdn.microsoft.com/library/windows/desktop/aa369820). Při instalaci sestavení vedle sebe jako soukromé sestavení, můžete jenom kopírovat odpovídající knihovny DLL, prostředky a sestavení manifestů jako součást procesu instalace do místní složky aplikace na cílovém počítači zajistit, že toto sestavení může být najít zavaděč za běhu (viz [pořadí hledání sestavení](/windows/desktop/SbsCs/assembly-searching-sequence)). Jinou možností je použít [Instalační služby systému Windows](/windows/desktop/Msi/windows-installer-portal) a postupujte podle pokynů uvedených v [instalaci sestavení Win32 pro soukromé použití aplikace na Windows XP](/windows/desktop/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp).

## <a name="see-also"></a>Viz také

[Příklady nasazení](../ide/deployment-examples.md)<br/>
[Sestavení izolovaných aplikací C/C++](../build/building-c-cpp-isolated-applications.md)<br/>
[Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)