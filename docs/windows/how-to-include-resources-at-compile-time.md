---
title: 'Postupy: zahrnutí prostředků v době kompilace (C++)'
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
ms.openlocfilehash: e931a0246340e81049df6ed0f8e26a4b91b570c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215188"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>Postupy: zahrnutí prostředků v době kompilace (C++)

Ve výchozím nastavení jsou všechny prostředky umístěny v jednom souboru skriptu prostředků (. RC), ale existuje mnoho důvodů, proč umístit prostředky do jiného souboru než do hlavního souboru. rc:

- Chcete-li přidat komentáře k příkazům prostředků, které se neodstraní při uložení souboru. rc.

- Zahrnutí prostředků, které již byly vyvinuty a testovány a nevyžadují další úpravy. Všechny soubory, které jsou zahrnuté, ale nemají rozšíření. RC, nebude možné upravovat pomocí editorů prostředků.

- Chcete-li zahrnout prostředky, které jsou používány různými projekty nebo které jsou součástí systému správy verzí zdrojového kódu. Tyto prostředky musí existovat v centrálním umístění, kde budou mít úpravy vliv na všechny projekty.

- Zahrnutí prostředků (například prostředků RCDATA), které jsou vlastním formátem. Prostředky RCDATA mají speciální požadavky, kde nemůžete použít výraz jako hodnotu pro pole `nameID`.

Pokud máte oddíly ve stávajících souborech. RC, které splňují některé z těchto podmínek, umístěte tyto oddíly do jednoho nebo více samostatných souborů. RC a zahrňte je do projektu pomocí dialogového okna **prostředek obsahuje** .

## <a name="resource-includes"></a>Prostředek zahrnuje

Do projektu můžete přidat prostředky z jiných souborů v době kompilace, a to tak, že je **uvedete** do pole **direktivy doby kompilace** v dialogovém okně prostředek. Pomocí dialogového okna **prostředek obsahuje** můžete upravit normální pracovní uspořádání prostředí projektu pro ukládání všech prostředků v souboru Project. RC a všech [symbolech](../windows/symbols-resource-identifiers.md) v `Resource.h`.

Chcete-li začít, otevřete dialogové okno **prostředek obsahuje** kliknutím pravým tlačítkem myši na soubor. rc v [prostředky](how-to-create-a-resource-script-file.md#create-resources), vyberte **prostředek zahrnuje** a vezměte v tomto seznamu následující vlastnosti:

| Vlastnost | Popis |
|---|---|
| **Soubor hlaviček symbolu** | Umožňuje změnit název hlavičkového souboru, ve kterém jsou uložené definice symbolů pro vaše soubory prostředků.<br/><br/>Další informace naleznete v tématu [Změna názvů souborů hlaviček symbolů](../windows/changing-the-names-of-symbol-header-files.md). |
| **Direktivy symbolů jen pro čtení** | Umožňuje zahrnout hlavičkové soubory, které obsahují symboly, které by se neměly upravovat.<br/><br/>Například soubory symbolů, které mají být sdíleny s jinými projekty. To může také zahrnovat soubory knihovny MFC. h. Další informace najdete v tématu [zahrnutí sdílených (jen pro čtení) nebo počítaných symbolů](../windows/including-shared-read-only-or-calculated-symbols.md). |
| **Direktivy při kompilaci** | Umožňuje zahrnout soubory prostředků, které jsou vytvořeny a upravovány odděleně od prostředků v hlavním souboru prostředků, obsahovat direktivy doby kompilace (například tyto směrnice, které podmíněně obsahují prostředky) nebo obsahují prostředky ve vlastním formátu.<br/><br/>Můžete také použít **pole direktivy pro kompilaci** k zahrnutí standardních souborů prostředků knihovny MFC. |

> [!NOTE]
> Položky v těchto textových polích se zobrazí v souboru. RC, který je označený `TEXTINCLUDE 1`, `TEXTINCLUDE 2`a `TEXTINCLUDE 3`. Další informace najdete v tématu [TN035: použití více souborů prostředků a hlavičkových souborů se C++sadou Visual ](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Jakmile provedete změny v souboru prostředků pomocí dialogového okna **prostředek obsahuje** , je nutné zavřít a znovu otevřít soubor *. RC* , aby se změny projevily.

### <a name="to-include-resources-in-your-project-at-compile-time"></a>Zahrnutí prostředků do projektu v době kompilace

1. Umístěte prostředky do souboru skriptu prostředků s jedinečným názvem souboru. Nepoužívejte *ProjectName. RC*, protože se jedná o název souboru používaného pro hlavní soubor skriptu prostředků.

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources) klikněte pravým tlačítkem na soubor *. RC* a vyberte **prostředek zahrnuje**.

1. V poli **direktivy pro kompilaci** přidejte direktivu [#include](../preprocessor/hash-include-directive-c-cpp.md) kompilátoru pro zahrnutí nového souboru prostředků do hlavního souboru prostředků ve vývojovém prostředí.

Prostředky v souborech, které jsou tímto způsobem zahrnuty, jsou pouze součástí spustitelného souboru v době kompilace a nejsou k dispozici pro úpravy ani úpravy při práci na hlavním souboru. RC projektu. Zahrnuté soubory. RC je nutné otevřít samostatně a všechny soubory zahrnuté bez rozšíření. RC nebude možné upravovat pomocí editorů prostředků.

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>Určení adresářů zahrnutí pro určitý soubor prostředků (. RC)

1. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor *. RC* a vyberte **vlastnosti**.

1. V levém podokně vyberte uzel **prostředky** a zadejte další adresáře zahrnutí do vlastnosti **Další adresáře pro zahrnutí** .

### <a name="to-find-symbols-in-resources"></a>Hledání symbolů v prostředcích

1. Přejděte na nabídku **upravit** > [Najít symbol](/visualstudio/ide/go-to).

   > [!TIP]
   > Chcete-li ve svém hledání použít [regulární výrazy](/visualstudio/ide/using-regular-expressions-in-visual-studio) , vyberte místo **hledání symbolu**možnost [najít v souborech](/visualstudio/ide/reference/find-command) v nabídce **Upravit** . Zaškrtněte políčko **použít regulární výrazy** v [dialogovém okně Najít](/visualstudio/ide/finding-and-replacing-text) a v poli **Najít** můžete zvolit regulární výraz hledání z rozevíracího seznamu. Když vyberete výraz z tohoto seznamu, nahradí se jako hledaný text v poli **Najít** .

1. V rozevíracím seznamu v poli **Najít** vyberte předchozí hledaný řetězec nebo zadejte klávesovou zkratku, kterou chcete najít, například `ID_ACCEL1`.

1. Vyberte některou z možností **hledání** a zvolte **Najít další**.

> [!NOTE]
> Symboly nelze hledat v řetězci, akcelerátoru nebo binárních prostředcích.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Postupy: vytváření prostředků](../windows/how-to-create-a-resource-script-file.md)<br/>
[Postupy: Správa prostředků](../windows/how-to-copy-resources.md)<br/>
