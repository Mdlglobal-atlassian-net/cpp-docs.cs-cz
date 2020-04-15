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
ms.openlocfilehash: de55059834a0887d487b7be38377af9984512b75
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336410"
---
# <a name="managing-a-library"></a>Správa knihovny

Výchozí režim pro LIB je vytvořit nebo upravit knihovnu objektů COFF. LIB spustí v tomto režimu, pokud nezadáte /EXTRACT (chcete-li zkopírovat objekt do souboru) nebo /DEF (chcete-li vytvořit knihovnu importu).

Chcete-li vytvořit knihovnu z objektů nebo knihoven, použijte následující syntaxi:

```
LIB [options...] files...
```

Tento příkaz vytvoří knihovnu z jednoho nebo více *vstupních souborů*. *Soubory* mohou být soubory objektů COFF, 32bitové objektové soubory OMF nebo existující knihovny COFF. LIB vytvoří jednu knihovnu, která obsahuje všechny objekty v určených souborech. Pokud je vstupní soubor 32bitový soubor objektu OMF, LIB jej před sestavením knihovny převede na COFF. LIB nemůže přijmout 32bitový objekt OMF, který je v knihovně vytvořené 16bitovou verzí LIB. K extrahování objektu je nutné nejprve použít 16bitovou LIB; pak můžete použít extrahovaný objektový soubor jako vstup do 32bitové LIB.

Ve výchozím nastavení lib pojmenuje výstupní soubor pomocí základního názvu prvního souboru objektu nebo knihovny a přípony .lib. Výstupní soubor je vložen do aktuálního adresáře. Pokud soubor již existuje se stejným názvem, výstupní soubor nahradí existující soubor. Chcete-li zachovat existující knihovnu, použijte možnost /OUT k určení názvu výstupního souboru.

Pro vytváření a úpravy knihovny platí následující možnosti:

**/LIBPATH:** *dir*<br/>
Přepíše cestu knihovny prostředí. Podrobnosti naleznete v popisu možnosti LINK [/LIBPATH.](libpath-additional-libpath.md)

**/SEZNAM**<br/>
Zobrazí informace o výstupní knihovně na standardní výstup. Výstup lze přesměrovat na soubor. Parametr /LIST můžete použít k určení obsahu existující knihovny bez úprav.

**/NAME:** *název souboru*<br/>
Při vytváření knihovny importu určuje název knihovny DLL, pro kterou se vytváří knihovna importu.

**/NODEFAULTLIB**<br/>
Odebere jednu nebo více výchozích knihoven ze seznamu knihoven, které hledá při řešení externích odkazů. Další informace naleznete [v tématu /NODEFAULTLIB.](nodefaultlib-ignore-libraries.md)

**/OUT:** *název souboru*<br/>
Přepíše výchozí výstupní název souboru. Ve výchozím nastavení je výstupní knihovna vytvořena v aktuálním adresáři se základním názvem první knihovny nebo souboru objektů na příkazovém řádku a příponou LIB.

**/REMOVE:** *objekt*<br/>
Vynese zadaný *objekt* z výstupní knihovny. LIB vytvoří výstupní knihovnu kombinací všech objektů (ať už v souborech objektů nebo knihovnách) a potom odstraní všechny objekty zadané pomocí /REMOVE.

**/SUBSYSTÉM:**{**KONZOLA** &#124; **EFI_APPLICATION** &#124; **EFI_APPLICATION EFI_BOOT_SERVICE_DRIVER** &#124; EFI_BOOT_SERVICE_DRIVER &#124; **EFI_ROM &#124;** &#124; EFI_RUNTIME_DRIVER **&#124;** &#124; **NATIVNÍ** &#124; **POSIX** &#124; &#124; **WINDOWSCE** }[#[.##]] **WINDOWSCE**<br/>
Říká operačnímu systému, jak spustit program vytvořený propojením s výstupní knihovnou. Další informace naleznete v popisu možnosti LINK [/SUBSYSTEM.](subsystem-specify-subsystem.md)

Možnosti LIB zadané na příkazovém řádku nerozlišují malá a velká písmena.

Lib můžete použít k provedení následujících úloh správy knihovny:

- Chcete-li přidat objekty do knihovny, zadejte název souboru pro existující knihovnu a názvy souborů pro nové objekty.

- Chcete-li kombinovat knihovny, zadejte názvy souborů knihovny. Můžete přidávat objekty a kombinovat knihovny s jedním příkazem LIB.

- Chcete-li nahradit člena knihovny novým objektem, zadejte knihovnu obsahující objekt člena, který má být nahrazen, a název souboru pro nový objekt (nebo knihovnu, která jej obsahuje). Pokud objekt se stejným názvem existuje ve více než jednom vstupním souboru, lib vloží poslední objekt zadaný v příkazu LIB do výstupní knihovny. Při nahrazení člena knihovny nezapomeňte zadat nový objekt nebo knihovnu za knihovnou, která obsahuje starý objekt.

- Chcete-li odstranit člena z knihovny, použijte možnost /REMOVE. LIB zpracovává všechny specifikace /REMOVE po kombinování všech vstupních objektů, bez ohledu na pořadí příkazového řádku.

> [!NOTE]
> Nemůžete odstranit člen a extrahovat jej do souboru ve stejném kroku. Nejprve je nutné extrahovat členský objekt pomocí /EXTRACT a potom znovu spustit LIB pomocí /REMOVE. Toto chování se liší od 16bitové LIB (pro knihovny OMF) poskytované v jiných produktech společnosti Microsoft.

## <a name="see-also"></a>Viz také

[Referenční dokumentace ke knihovně LIB](lib-reference.md)
