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
ms.openlocfilehash: 06ad2f90e7e72492f1e6ca4000a6c101fc36b205
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320663"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>Postupy: Zahrnutí prostředků v době kompilace (C++)

Obvykle je snadný a pohodlný pro práci s výchozí uspořádání všech prostředků v jednom souboru prostředku skriptů (.rc). Existují však několik důvodů, proč umístit prostředky do souboru než hlavní .rc souborů:

- Chcete-li přidat komentáře pro příkazy prostředků, které nebudou se odstraní při ukládání souboru .rc.

   Editory prostředků přímo si .rc nebo `resource.h` soubory. Nástroj resource compiler jejich kompiluje do soubory .aps, které se spotřebovávají editory prostředků. Tento soubor je kompilační krok a ukládá pouze datový symbolické. Jako normální zkompilovat procesu, se zahodí informace, které nejsou symbolické (například komentáře) v průběhu kompilace. Pokaždé, když se soubor .aps získá synchronizována se soubor .rc, se znovu vygeneroval soubor .rc (například když uložíte, editor prostředků přepíše soubor .rc a `resource.h` souboru). Všechny změny samotné prostředky zůstanou zahrnuté v souboru .rc, ale komentáře vždy ztratí dojde k přepsání souboru .rc.

- Chcete zahrnout prostředky, které již byly vývoji a testování a nepotřebují další úpravy. (Všechny soubory, které jsou zahrnuty, ale nemají příponou .rc nebude možné upravovat podle editory prostředků.)

- Chcete zahrnout prostředky, které se používají v několika různých projektech, nebo jsou součástí systému správy verzí zdrojového kódu a tedy musí existovat v centrálním umístění, kde změny bude mít vliv na všechny projekty.

- Chcete zahrnout prostředky (jako jsou například prostředky RCDATA), které jsou ve vlastním formátu. RCDATA prostředky mohou mít zvláštní požadavky. Například nelze použít výraz jako hodnotu pro pole nameID. Další informace najdete v dokumentaci Windows SDK.

## <a name="resource-includes"></a>Prostředek zahrnuje

Můžete přidat prostředky v jiných souborech do aktuálního projektu v době kompilace v jejich uvedení v seznamu **směrnice času kompilace** pole **prostředek zahrnuje** dialogové okno.

Pokud máte oddíly v existujících souborech .rc, které splňují kterákoli z těchto podmínek, měli byste umístit v oddílech v jednom nebo více samostatných souborů .rc a zahrnout je do projektu pomocí **prostředek zahrnuje** dialogové okno. *Projectname*.rc2 soubor vytvořený v podadresáři \res nový projekt se používá pro tento účel.

Můžete použít **prostředek zahrnuje** dialogové okno projektu v jazyce C++ upravit prostředí normální funkční uspořádání ukládání všech prostředků v projektu soubor .rc a všechny [symboly](../windows/symbols-resource-identifiers.md) v souboru Resource.h.

Chcete-li otevřít **prostředek zahrnuje** dialogové okno, klikněte pravým tlačítkem na příslušný .rc souborů v [zobrazení prostředků](../windows/resource-view-window.md), klikněte na tlačítko **prostředek zahrnuje** z místní nabídky. Viz následující vlastnosti:

|Vlastnost|Popis|
|--|----|
|**Hlavičkový soubor symbolů**|Umožňuje změnit název hlavičkového souboru, kde jsou uloženy definice symbolů pro váš soubor prostředků. Další informace najdete v tématu [mění se názvy z hlavičkových souborů symbolu](../windows/changing-the-names-of-symbol-header-files.md).|
|**Směrnice souborů jen pro čtení**|Umožňuje zahrnout soubory hlaviček, které obsahují symboly, které by se nemělo upravovat během úprav relace. Například můžete zahrnout soubor se symboly, jež jsou sdílena mezi několika projekty. Můžete také zahrnout soubory hlaviček knihovny MFC. Další informace najdete v tématu [zahrnutí sdílených (jen pro čtení) nebo počítané symboly](../windows/including-shared-read-only-or-calculated-symbols.md).|
|**Směrnice času kompilace**|Umožňuje zahrnout soubory prostředků, které vytvářejí se a upravují samostatně z prostředků v hlavní soubor prostředků, obsahovat směrnice času kompilace (jako jsou uvedené směrnice, které podmíněně zahrnout prostředky), nebo obsahují prostředky ve vlastním formátu. Můžete také použít **pole direktivy kompilace** mají zahrnout soubory prostředků standardní knihovny MFC.|

> [!NOTE]
> Zobrazí položky v těchto textových polí v souboru .rc, které jsou označené nástrojem `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, a `TEXTINCLUDE 3` v uvedeném pořadí. Další informace najdete v tématu [TN035: Použití více zdrojových souborů a hlavičkových souborů v jazyce Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Jakmile se změny provedené pomocí souboru prostředků **prostředek zahrnuje** dialogové okno, budete muset zavřít soubor .rc a znovu ho, aby se změny projevily.

### <a name="to-include-resources-in-your-project-at-compile-time"></a>Chcete zahrnout prostředky ve vašem projektu v době kompilace

1. Umístíte prostředky v souboru skriptu prostředků s jedinečným názvem souboru. Nepoužívejte *projectname*.rc, protože tento název se používá pro soubor skriptu prostředku hlavní název souboru.

1. Klikněte pravým tlačítkem na soubor .rc (v [zobrazení prostředků](../windows/resource-view-window.md)) a zvolte **prostředek zahrnuje** z místní nabídky.

1. V **směrnice času kompilace** přidejte [#include](../preprocessor/hash-include-directive-c-cpp.md) direktivy kompilátoru zahrnout nový soubor prostředků hlavního souboru prostředku ve vývojovém prostředí.

   Prostředky v souborech tímto způsobem jsou součástí vašeho spustitelného souboru k v době kompilace. Nejsou přímo k dispozici pro úpravy nebo změny při práci na souboru .rc hlavního projektu. Otevřete soubory zahrnuté .rc odděleně. Všechny soubory, které jsou zahrnuty, ale nemají příponou .rc nebude možné upravovat podle editory prostředků.

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>K určení adresářů include pro konkrétní prostředek (soubor .rc)

1. Klikněte pravým tlačítkem na soubor .rc v Průzkumníku řešení a vyberte **vlastnosti** z místní nabídky.

1. Vyberte **prostředky** uzlu v levém podokně a určete všechny další adresáře include **další adresáře souborů k zahrnutí** vlastnost.

### <a name="to-find-symbols-in-resources"></a>Chcete-li najít symboly v prostředcích

1. Z **upravit** nabídce zvolte [najít Symbol](/visualstudio/ide/go-to).

1. V **najít** pole, vyberte předchozí hledaný řetězec z rozevíracího seznamu nebo zadejte klíče akcelerátoru, které chcete najít (například `ID_ACCEL1`).

   > [!TIP]
   > Použití [regulární výrazy](/visualstudio/ide/using-regular-expressions-in-visual-studio) pro hledání, je nutné použít [najít v souborech – příkaz](/visualstudio/ide/reference/find-command) z **upravit** nabídky místo **najít Symbol**příkazu. Pokud chcete povolit regulárních výrazů, musíte mít **použití: Regulární výrazy** zaškrtnuto políčko [dialogové okno hledání](/visualstudio/ide/finding-and-replacing-text). Potom můžete vybrat tlačítko se šipkou vpravo na pravé straně **najít** pole k zobrazení seznamu hledání regulárních výrazů. Když vyberete výrazu z tohoto seznamu, je nahrazen jako hledaný text v **najít** pole.

1. Vyberte některou z **najít** možnosti a vyberte **najít další**.

> [!NOTE]
> Nelze hledat symboly v řetězci, akcelerátoru nebo binární prostředky.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Vytvoření prostředků](../windows/how-to-create-a-resource-script-file.md)<br/>
[Správa prostředků](../windows/how-to-copy-resources.md)<br/>