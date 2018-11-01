---
title: Správa knihovny
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLibrarianTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLibrarianTool.AdditionalDependencies
- VC.Project.VCLibrarianTool.RemoveObjects
- VC.Project.VCLibrarianTool.LibraryPaths
- VC.Project.VCLibrarianTool.OutputFile
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryNames
- VC.Project.VCLibrarianTool.AdditionalLibraryDirectories
- VC.Project.VCLibrarianTool.ListContentsFile
- VC.Project.VCLibrarianTool.ListContents
- VC.Project.VCLibrarianTool.SubSystemVersion
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryName
- VC.Project.VCLibrarianTool.SubSystem
helpviewer_keywords:
- /LIBPATH library manager option
- OUT library manager option
- CONVERT library manager option
- LIBPATH library manager option
- /LIST library manager option
- object files, building and modifying
- -LINK50COMPAT library manager option
- REMOVE library manager option
- SUBSYSTEM library manager option
- /LINK50COMPAT library manager option
- /OUT library manager option
- LIB [C++], managing COFF libraries
- -CONVERT library manager option
- LINK50COMPAT library manager option
- -OUT library manager option
- -REMOVE library manager option
- -LIST library manager option
- /SUBSYSTEM library manager option
- -SUBSYSTEM library manager option
- /REMOVE library manager option
- -LIBPATH library manager option
- object files
- LIST library manager option
- /CONVERT library manager option
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
ms.openlocfilehash: 69cd03e029d014b9b74a8688f155dfb1f023b55c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477061"
---
# <a name="managing-a-library"></a>Správa knihovny

K vytvoření nebo úpravě knihovnu objektů COFF je výchozí režim pro LIB. LIB běží v tomto režimu, když zadáte/extract (Chcete-li zkopírovat do souboru objektu) nebo def (k sestavení knihovny importu).

Pokud chcete vytvořit knihovnu z objektů nebo knihoven, použijte následující syntaxi:

```
LIB [options...] files...
```

Tento příkaz vytvoří knihovnu z jednoho nebo více vstupních *soubory*. *Soubory* může být soubory objektů COFF, 32 bitů omf – soubory objektů nebo existujících knihoven COFF. LIB vytvoří jedna knihovna, která obsahuje všechny objekty v zadaných souborů. Pokud vstupní soubor je soubor objektu omf – 32-bit, LIB převede ho na COFF před vytvořením knihovny. LIB nemůže přijmout objekt omf – 32-bit, který je uložený v knihovně vytvořené v 16bitové verzi produktu LIB. 16bitové LIB musíte nejprve použít k extrahování objekt. Soubor byl extrahován objektu můžete použít jako vstup pro nástroj LIB 32-bit.

Ve výchozím nastavení, LIB názvy výstupního souboru pomocí základní název prvního souboru objektů nebo knihoven a příponou. lib. Výstupní soubor je umístěn v aktuálním adresáři. Pokud soubor se stejným názvem už existuje, výstupní soubor nahradí existující soubor. Pokud chcete zachovat existující knihovnu, použijte možnost parametr/out a zadat název výstupního souboru.

Tyto možnosti platí pro vytváření a úpravy knihovny:

**/ LIBPATH:** *dir*<br/>
Přepíše cestu ke knihovně prostředí. Podrobnosti najdete v tématu Popis odkazu [/Libpath](../../build/reference/libpath-additional-libpath.md) možnost.

**/ LIST**<br/>
Zobrazí informace o výstupní knihovně na standardním výstupu. Výstup je možné přesměrovat do souboru. / List můžete zjistit obsah stávající knihovny bez její změny.

**/ NAME:** *název souboru*<br/>
Při sestavování knihovny importů Určuje název knihovny DLL pro kterou má být sestaven knihovny importu.

**/ NODEFAULTLIB**<br/>
Odebere jeden nebo více výchozích knihoven ze seznamu knihoven, které prohledává při překladu externích odkazů. Zobrazit [: / NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) Další informace.

**/ OUT:** *název souboru*<br/>
Přepíše výchozí název výstupního souboru. Ve výchozím nastavení je výstupní knihovně vytvoří v aktuálním adresáři se základním názvem první knihovny objektu souboru nebo na příkazovém řádku a rozšíření. lib.

**/ REMOVE:** *objektu*<br/>
Vynechá zadaný *objekt* z výstupní knihovně. LIB vytvoří výstupní knihovnu tak, že zkombinuje všechny objekty (ať už v souborech objektů nebo knihoven) a poté odstraní všechny objekty zadané pomocí parametru/remove.

**/ SUBSYSTEM:**{**KONZOLY** &AMP;#124; **EFI_APPLICATION** &AMP;#124; **BITOVÁ KOPIE EFI_BOOT_SERVICE_DRIVER** &AMP;#124; **EFI_ROM** &AMP;#124; **EFI_RUNTIME_DRIVER** &AMP;#124; **NATIVNÍ** &AMP;#124; **POSIX** &AMP;#124; **WINDOWS** &AMP;#124; **WINDOWSCE**} [, #[. ##]]<br/>
Říká operačnímu systému, jak spustit program vytvořil připojování ke knihovně výstup. Další informace naleznete v popisu odkaz [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) možnost.

Lib – možnosti zadané v příkazovém řádku se nerozlišují malá a velká písmena.

Můžete provádět následující úlohy správy knihovny LIB:

- Chcete-li přidat objekty do knihovny, zadejte název souboru pro existující knihovnu a názvy souborů pro nové objekty.

- Kombinování knihovny, zadejte názvy souborů knihovny. Můžete přidat objekty a knihovny v kombinaci s jediným příkazem LIB.

- Nahraďte členem knihovny nový objekt, zadejte knihovna, která obsahuje člen objektu, který chcete nahradit a název souboru pro nový objekt (nebo knihovnu, která ji obsahuje). Objekt, který má stejný název ve více než jeden vstupní soubor existuje, LIB vloží poslední objekt určený v příkazu LIB do výstupní knihovně. Když nahradíte člena knihovny, nezapomeňte zadat nový objekt nebo knihovny po knihovnu, která obsahuje původní objekt.

- Pokud chcete odstranit člena z knihovny, použijte možnost/Remove. Lib – zpracovává všechny specifikace parametru/Remove po zkombinuje všechny objekty vstupní, bez ohledu na to, příkazového řádku pořadí.

> [!NOTE]
>  Nelze současně odstraní člena a rozbalte ho do souboru do jednoho kroku. Nejdřív musíte extrahovat členského objektu pomocí/extract a potom spusťte LIB znovu pomocí parametru/remove. Toto chování se liší od 16 bitů LIB (pro knihovny OMF) k dispozici v jiných produktů Microsoftu.

## <a name="see-also"></a>Viz také

[Referenční dokumentace ke knihovně LIB](../../build/reference/lib-reference.md)