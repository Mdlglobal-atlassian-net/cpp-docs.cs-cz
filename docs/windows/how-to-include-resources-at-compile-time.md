---
title: 'Postupy: Zahrnutí prostředků v době kompilace (C++)'
ms.date: 02/14/2019
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
- vc.editors.resourceincludes
helpviewer_keywords:
- comments [C++], compiled files
- resources [C++], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
- directories [C++], specifying include paths for resources
- include files [C++], specifying for resources
- resources [C++], including in projects
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: ca24a10f905e61feb2b090ba3966c752db3d4444
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350920"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>Postupy: Zahrnutí prostředků v době kompilace (C++)

Ve výchozím nastavení všechny prostředky jsou umístěné v jednom souboru prostředku skriptů (.rc) ale existuje mnoho důvodů umístit prostředky do souboru než hlavní .rc souborů:

- Chcete-li přidat komentáře pro příkazy prostředků, které nebudou se odstraní při ukládání souboru .rc.

- Chcete zahrnout prostředky, které již byly vývoji a testování a nepotřebují další úpravy. Všechny soubory, které jsou zahrnuty, ale nemají příponou .rc nebude možné upravovat podle editory prostředků.

- Chcete zahrnout prostředky, které se používají v různých projektech, nebo které jsou součástí systému správy verzí zdrojového kódu. Tyto prostředky musí existovat v centrálním umístění, kde změny bude mít vliv na všechny projekty.

- Chcete zahrnout prostředky (jako jsou například prostředky RCDATA), které jsou vlastního formátu. Prostředky RCDATA mají speciální požadavky, ve kterém nelze použít výraz jako hodnotu `nameID` pole.

Pokud máte oddíly v existujících souborech .rc, které splňují kterákoli z těchto podmínek, umístěte tyto části do jedné nebo více samostatných souborů .rc a zahrnout je do projektu pomocí **prostředek zahrnuje** dialogové okno.

## <a name="resource-includes"></a>Prostředek zahrnuje

Můžete přidat prostředky z jiných souborů do projektu v době kompilace v jejich uvedení v seznamu **směrnice času kompilace** pole **prostředek zahrnuje** dialogové okno. Použití **prostředek zahrnuje** dialogové okno Upravit prostředí projektu normální funkční uspořádání ukládání všech prostředků v projektu soubor .rc a všechny [symboly](../windows/symbols-resource-identifiers.md) v `Resource.h`.

Chcete-li začít, otevřete **prostředek zahrnuje** dialogové okno kliknutím pravým tlačítkem myši v souboru .rc [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources)vyberte **prostředek zahrnuje** a mějte na paměti následující vlastnosti:

| Vlastnost | Popis |
|---|---|
| **Hlavičkový soubor symbolů** | Umožňuje změnit název hlavičkového souboru, kde jsou uloženy definice symbolů pro vaše soubory prostředků.<br/><br/>Další informace najdete v tématu [mění se názvy z hlavičkových souborů symbolu](../windows/changing-the-names-of-symbol-header-files.md). |
| **Směrnice souborů jen pro čtení** | Umožňuje zahrnout soubory hlaviček, které obsahují symboly, které by se nemělo upravovat.<br/><br/>Například soubory symbolů ke sdílení s jinými projekty. To může zahrnovat souborech hlaviček knihovny MFC. Další informace najdete v tématu [zahrnutí sdílených (jen pro čtení) nebo počítané symboly](../windows/including-shared-read-only-or-calculated-symbols.md). |
| **Směrnice času kompilace** | Umožňuje zahrnout soubory prostředků, které vytvářejí se a upravují samostatně z prostředků v hlavní soubor prostředků, obsahovat směrnice času kompilace (jako jsou uvedené směrnice, které podmíněně zahrnout prostředky), nebo obsahují prostředky ve vlastním formátu.<br/><br/>Můžete také použít **pole direktivy kompilace** mají zahrnout soubory prostředků standardní knihovny MFC. |

> [!NOTE]
> Zobrazí položky v těchto textových polí v souboru .rc, které jsou označené nástrojem `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, a `TEXTINCLUDE 3` v uvedeném pořadí. Další informace najdete v tématu [TN035: Použití více zdrojových souborů a hlavičkových souborů v jazyce Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Po provedení změn pomocí souboru prostředků **prostředek zahrnuje** dialogové okno, musíte zavřít a znovu otevřít *.rc* souboru, aby se změny projevily.

### <a name="to-include-resources-in-your-project-at-compile-time"></a>Chcete zahrnout prostředky ve vašem projektu v době kompilace

1. Umístíte prostředky v souboru skriptu prostředků s jedinečným názvem souboru. Nepoužívejte *projectname.rc*, protože jde o název souboru pro soubor skriptu hlavní prostředku.

1. Klikněte pravým tlačítkem myši *.rc* ve [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources) a vyberte **prostředek zahrnuje**.

1. V **směrnice času kompilace** přidejte [#include](../preprocessor/hash-include-directive-c-cpp.md) direktivy kompilátoru zahrnout nový soubor prostředků hlavního souboru prostředku ve vývojovém prostředí.

Prostředky v souborech tímto způsobem jsou prováděny pouze část spustitelný soubor v době kompilace a nejsou k dispozici pro úpravy nebo změny při práci na souboru .rc hlavního projektu. Soubory zahrnuté .rc muset otevřít samostatně a všechny soubory zahrnuté bez přípony .rc nebude možné upravovat podle editory prostředků.

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>K určení adresářů include pro soubor konkrétních prostředků (.rc)

1. Klikněte pravým tlačítkem myši *.rc* ve **Průzkumníka řešení** a vyberte **vlastnosti**.

1. Vyberte **prostředky** uzlu v levém podokně a určete všechny další adresáře include **další adresáře souborů k zahrnutí** vlastnost.

### <a name="to-find-symbols-in-resources"></a>Chcete-li najít symboly v prostředcích

1. Přejděte do nabídky **upravit** > [najít Symbol](/visualstudio/ide/go-to).

   > [!TIP]
   > Použití [regulární výrazy](/visualstudio/ide/using-regular-expressions-in-visual-studio) při hledání, vyberte [najít v souborech](/visualstudio/ide/reference/find-command) v **upravit** nabídky místo **najít Symbol**. Vyberte **použití: Regulární výrazy** zaškrtávací políčko [dialogové okno hledání](/visualstudio/ide/finding-and-replacing-text) a **najít** hledaný regulární výraz lze vybírat z rozevíracího seznamu. Když vyberete výrazu z tohoto seznamu, je nahrazen jako hledaný text v **najít** pole.

1. V **najít** pole, vyberte předchozí hledaný řetězec z rozevíracího seznamu nebo zadejte klíče akcelerátoru, které chcete najít, například `ID_ACCEL1`.

1. Vyberte některou z **najít** možnosti a vyberte **najít další**.

> [!NOTE]
> Nelze hledat symboly v řetězci, akcelerátoru nebo binární prostředky.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Postupy: Vytvořit prostředky](../windows/how-to-create-a-resource-script-file.md)<br/>
[Postupy: Spravovat prostředky](../windows/how-to-copy-resources.md)<br/>