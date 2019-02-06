---
title: 'Postupy: Zahrnutí prostředků v době kompilace (C++)'
ms.date: 11/04/2016
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
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: 52145d2a656a7cac0d07a43ceaf298fbebb5ad40
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55764074"
---
# <a name="how-to-include-resources-at-compile-time"></a>Postupy: Zahrnutí prostředků v době kompilace

Obvykle je snadný a pohodlný pro práci s výchozí uspořádání všech prostředků v jednom souboru prostředku skriptů (.rc). Ale můžete přidat prostředky v jiných souborech do aktuálního projektu v době kompilace v jejich uvedení v seznamu **směrnice času kompilace** pole **prostředek zahrnuje** dialogové okno.

Tady je několik důvodů umístit prostředky do souboru než hlavní .rc souborů:

- Chcete-li přidat komentáře pro příkazy prostředků, které nebudou se odstraní při ukládání souboru .rc.

   Editory prostředků přímo si .rc nebo `resource.h` soubory. Nástroj resource compiler jejich kompiluje do soubory .aps, které se spotřebovávají editory prostředků. Tento soubor je kompilační krok a ukládá pouze datový symbolické. Jako normální zkompilovat procesu, se zahodí informace, které nejsou symbolické (například komentáře) v průběhu kompilace. Pokaždé, když se soubor .aps získá synchronizována se soubor .rc, se znovu vygeneroval soubor .rc (například když uložíte, editor prostředků přepíše soubor .rc a `resource.h` souboru). Všechny změny samotné prostředky zůstanou zahrnuté v souboru .rc, ale komentáře vždy ztratí dojde k přepsání souboru .rc.

- Chcete zahrnout prostředky, které již byly vývoji a testování a nepotřebují další úpravy. (Všechny soubory, které jsou zahrnuty, ale nemají příponou .rc nebude možné upravovat podle editory prostředků.)

- Chcete zahrnout prostředky, které se používají v několika různých projektech, nebo jsou součástí systému správy verzí zdrojového kódu a tedy musí existovat v centrálním umístění, kde změny bude mít vliv na všechny projekty.

- Chcete zahrnout prostředky (jako jsou například prostředky RCDATA), které jsou ve vlastním formátu. RCDATA prostředky mohou mít zvláštní požadavky. Například nelze použít výraz jako hodnotu pro pole nameID. V dokumentaci Windows SDK pro další informace.

Pokud máte oddíly v existujících souborech .rc, které splňují kterákoli z těchto podmínek, měli byste umístit v oddílech v jednom nebo více samostatných souborů .rc a zahrnout je do projektu pomocí **prostředek zahrnuje** dialogové okno. *Projectname*.rc2 soubor vytvořený v podadresáři \res nový projekt se používá pro tento účel.

Můžete použít **prostředek zahrnuje** dialogové okno projektu v jazyce C++ upravit prostředí normální funkční uspořádání ukládání všech prostředků v projektu soubor .rc a všechny [symboly](../windows/symbols-resource-identifiers.md) v souboru Resource.h.

Chcete-li otevřít **prostředek zahrnuje** dialogové okno, klikněte pravým tlačítkem na příslušný .rc souborů v [zobrazení prostředků](../windows/resource-view-window.md), klikněte na tlačítko **prostředek zahrnuje** z místní nabídky. Dialogové okno obsahuje následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Hlavičkový soubor symbolů**|Umožňuje změnit název hlavičkového souboru, kde jsou uloženy definice symbolů pro váš soubor prostředků. Další informace najdete v tématu [mění se názvy z hlavičkových souborů symbolu](../windows/changing-the-names-of-symbol-header-files.md).|
|**Směrnice souborů jen pro čtení**|Umožňuje zahrnout soubory hlaviček, které obsahují symboly, které by se nemělo upravovat během úprav relace. Například můžete zahrnout soubor se symboly, jež jsou sdílena mezi několika projekty. Můžete také zahrnout soubory hlaviček knihovny MFC. Další informace najdete v tématu [zahrnutí sdílených (jen pro čtení) nebo počítané symboly](../windows/including-shared-read-only-or-calculated-symbols.md).|
|**Směrnice času kompilace**|Umožňuje zahrnout soubory prostředků, které vytvářejí se a upravují samostatně z prostředků v hlavní soubor prostředků, obsahovat směrnice času kompilace (jako jsou uvedené směrnice, které podmíněně zahrnout prostředky), nebo obsahují prostředky ve vlastním formátu. Můžete také použít **pole direktivy kompilace** mají zahrnout soubory prostředků standardní knihovny MFC. Další informace najdete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).|

> [!NOTE]
> Zobrazí položky v těchto textových polí v souboru .rc, které jsou označené nástrojem `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, a `TEXTINCLUDE 3` v uvedeném pořadí. Další informace najdete v tématu [TN035: Použití více zdrojových souborů a hlavičkových souborů v jazyce Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Jakmile se změny provedené pomocí souboru prostředků **prostředek zahrnuje** dialogové okno, budete muset zavřít soubor .rc a znovu ho, aby se změny projevily. Další informace najdete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v rozhraní .NET Framework Developer's Guide.

## <a name="to-include-resources-in-your-project-at-compile-time"></a>Chcete zahrnout prostředky ve vašem projektu v době kompilace

1. Umístíte prostředky v souboru skriptu prostředků s jedinečným názvem souboru. Nepoužívejte *projectname*.rc, protože tento název se používá pro soubor skriptu prostředku hlavní název souboru.

1. Klikněte pravým tlačítkem na soubor .rc (v [zobrazení prostředků](../windows/resource-view-window.md)) a zvolte **prostředek zahrnuje** z místní nabídky.

1. V **směrnice času kompilace** přidejte [#include](../preprocessor/hash-include-directive-c-cpp.md) direktivy kompilátoru zahrnout nový soubor prostředků hlavního souboru prostředku ve vývojovém prostředí.

   Prostředky v souborech tímto způsobem jsou součástí vašeho spustitelného souboru k v době kompilace. Nejsou přímo k dispozici pro úpravy nebo změny při práci na souboru .rc hlavního projektu. Otevřete soubory zahrnuté .rc odděleně. Všechny soubory, které jsou zahrnuty, ale nemají příponou .rc nebude možné upravovat podle editory prostředků.

## <a name="to-specify-include-directories-for-a-specific-resource-rc-file-c"></a>K určení adresářů include pro konkrétní prostředek (soubor .rc) (C++)

1. Klikněte pravým tlačítkem na soubor .rc v Průzkumníku řešení a vyberte **vlastnosti** z místní nabídky.

1. V **stránky vlastností** dialogové okno, vyberte **prostředky** uzlu v levém podokně, pak zadejte další adresáře include **Další zahrnuté adresáře**vlastnost.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)<br/>
[TN035: Použití více zdrojových souborů a hlavičkových souborů v jazyce Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)<br/>
[Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)<br/>
