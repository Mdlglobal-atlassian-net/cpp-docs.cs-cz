---
title: Editor řetězců (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.string.F1
- vc.editors.string
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
- strings [C++], searching
- strings [C++]
- strings [C++], adding to string tables
- string tables [C++], deleting strings
- strings [C++], deleting in string tables
- string tables [C++], adding strings
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
ms.openlocfilehash: 996e5f132e5cfa33c39c4cc3ddbeb692f41925bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514713"
---
# <a name="string-editor-c"></a>Editor řetězců (C++)

Tabulka řetězců je prostředek systému Windows, který obsahuje seznam identifikátorů, hodnot a titulků pro všechny řetězce vaší aplikace. Například výzvy stavového řádku jsou umístěny v tabulce řetězců.

Při vývoji aplikace můžete mít několik tabulek řetězců – jeden pro každý jazyk nebo podmínku. Spustitelný modul však má pouze jednu tabulku řetězců. Běžící aplikace může odkazovat na několik tabulek řetězců, pokud tabulky vložíte do různých knihoven DLL.

Tabulky řetězců usnadňují lokalizaci vaší aplikace do různých jazyků. Pokud jsou všechny řetězce v tabulce řetězců, lze lokalizovat aplikace pomocí překladu řetězců (a dalších prostředků) bez změny zdrojového kódu. Tato situace je vhodnější než ruční vyhledávání a nahrazování různých řetězců ve zdrojových souborech.

> [!NOTE]
> Windows neumožňuje vytváření prázdných tabulek řetězců. Pokud vytvoříte tabulku řetězců bez zadání, při uložení souboru prostředků se odstraní automaticky.

## <a name="how-to"></a>Postupy

**Editor řetězců** vám umožní:

### <a name="to-find-a-string-resource-in-the-string-table"></a>Vyhledání prostředku řetězce v tabulce řetězců

1. Otevřete tabulku řetězců dvojitým kliknutím na její ikonu v [prostředky](how-to-create-a-resource-script-file.md#create-resources).

1. Přejděte do nabídky **Upravit** > **Najít a nahradit** a vyberte **Najít**.

1. V rozevíracím seznamu **Najít** vyberte předchozí hledaný řetězec nebo zadejte text titulku nebo identifikátor prostředku řetězce, který chcete najít.

1. Vyberte některou z možností **hledání** a vyberte **Najít další**.

> [!TIP]
> Chcete-li při hledání souborů použít [regulární výrazy](/visualstudio/ide/using-regular-expressions-in-visual-studio) , použijte příkaz **najít v souborech** v nabídce **Upravit** .
>
> Zadejte regulární výraz, který bude odpovídat vzoru, nebo vyberte tlačítko napravo od pole **Najít** , chcete-li zobrazit seznam regulárních výrazů hledání. Když vyberete výraz z tohoto seznamu, nahradí se jako hledaný text v poli **Najít** .
>
> Pokud používáte regulární výrazy, ujistěte se, že **používáte: Zaškrtávací políčko** regulární výrazy je zaškrtnuto.

### <a name="to-add-or-delete-a-string-resource"></a>Přidání nebo odstranění prostředku řetězce

Můžete rychle vložit nebo odstranit položky do tabulky řetězců pomocí **editoru řetězců**. Nové řetězce jsou umístěny na konci tabulky a mají k dispozici další dostupný identifikátor. Podle potřeby můžete upravit vlastnosti **ID**, **hodnoty**nebo **popisku** v [okno Vlastnosti](/visualstudio/ide/reference/properties-window) .

**Editor řetězců** zajišťuje, že nepoužíváte ID, které se už používá. Pokud vyberete ID, které se už používá, **Editor řetězců** vás upozorní a pak přiřadí obecné jedinečné ID, `IDS_STRING58113`například.

#### <a name="to-add-a-string-table-entry"></a>Přidání položky tabulky řetězců

1. Otevřete tabulku řetězců dvojitým kliknutím na její ikonu v [prostředky](how-to-create-a-resource-script-file.md#create-resources).

1. Klikněte pravým tlačítkem v tabulce řetězců a vyberte **nový řetězec**.

1. V **editoru řetězců**vyberte **ID** z rozevíracího seznamu **ID** nebo zadejte *ID* přímo na místě.

1. V případě potřeby upravte **hodnotu**.

1. Zadejte položku pro **Titulek**.

   > [!NOTE]
   > V tabulkách řetězců systému Windows nejsou povoleny řetězce s hodnotou null. Pokud vytvoříte položku v tabulce řetězců, která je prázdným řetězcem, zobrazí se zpráva s výzvou, abyste **zadali řetězec pro tuto položku tabulky**.

#### <a name="to-delete-a-string-table-entry"></a>Odstranění položky tabulky řetězců

Vyberte položku, kterou chcete odstranit, a proveďte jednu z následujících akcí:

- Přejděte na nabídku **Upravit** > **odstranění**.

- Klikněte pravým tlačítkem na řetězec, který chcete odstranit, a vyberte **Odstranit**.

- Stiskněte klávesu **Delete** .

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Přesunutí řetězce z jednoho souboru skriptu prostředků do jiného

1. [V souborech. RC otevřete tabulky řetězců](../windows/how-to-create-a-resource-script-file.md).

1. Klikněte pravým tlačítkem myši na řetězec, který chcete přesunout, a vyberte **Vyjmout**.

1. Umístěte kurzor do okna Editor cílového **řetězce** .

1. V souboru *. RC* , do kterého chcete přesunout řetězec, klikněte pravým tlačítkem myši a vyberte možnost **Vložit**.

> [!NOTE]
> Pokud je **ID** nebo **hodnota** přesunutého řetězce v konfliktu s existujícím **ID** nebo **hodnotou** v cílovém souboru, buď se změní **identifikátor** nebo **hodnota** přesunutého řetězce.

### <a name="to-change-the-properties-of-a-string-resource"></a>Změna vlastností prostředku řetězce

Pomocí místních úprav můžete změnit vlastnosti **ID**, **hodnoty**a **titulku** .

> [!NOTE]
>  Můžete také upravit vlastnosti řetězce v [okno Vlastnosti](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-a-string-or-its-identifier"></a>Změna řetězce nebo jeho identifikátoru

1. Otevřete tabulku řetězců dvojitým kliknutím na její ikonu v [prostředky](how-to-create-a-resource-script-file.md#create-resources).

1. Vyberte řetězec, který chcete upravit, a dvakrát klikněte na sloupec **ID**, **hodnota**nebo **Titulek** a pak můžete:

   - V rozevíracím seznamu **ID** vyberte **ID** nebo zadejte *ID* přímo na místě.

   - Do sloupce **hodnota** zadejte jiné číslo.

   - Do sloupce titulku zadejte úpravy.

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Změna vlastnosti titulku prostředků s více řetězci

1. Otevřete tabulku řetězců dvojitým kliknutím na její ikonu v [prostředky](how-to-create-a-resource-script-file.md#create-resources).

1. Vyberte řetězce, které chcete změnit, a podržením klávesy **CTRL** při výběru každého z nich.

1. V [okně Vlastnosti](/visualstudio/ide/reference/properties-window)zadejte novou hodnotu vlastnosti, kterou chcete změnit.

1. Stisknutím klávesy **zadejte**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Přidání formátování nebo speciálních znaků do prostředku řetězce

1. Otevřete tabulku řetězců dvojitým kliknutím na její ikonu v [prostředky](how-to-create-a-resource-script-file.md#create-resources).

1. Vyberte řetězec, který chcete upravit.

1. V [okně Vlastnosti](/visualstudio/ide/reference/properties-window)přidejte všechny standardní řídicí sekvence uvedené níže do textu v poli **Titulek** a stiskněte klávesu **ENTER**.

   |K získání...|Zadejte tuto...|
   |-----------------|---------------|
   | Nový řádek | \\n |
   | Návrat na začátek řádku | \\r |
   | Karta | \\t |
   | Zpětné lomítko\\() | \\\\ |
   | Znak ASCII | \\DDD (osmičkový zápis) |
   | Upozornění (zvonek) | \\a |

   > [!NOTE]
   > **Editor řetězce** nepodporuje úplnou sadu řídicích asci znaků. Můžete použít jenom ty, které jsou uvedené výše.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[](../windows/resource-editors.md)
[Řetězce](/windows/win32/menurc/strings) editorů prostředků<br/>
[O řetězcích](/windows/win32/menurc/about-strings)<br/>
[Přizpůsobení rozložení oken](/visualstudio/ide/customizing-window-layouts-in-visual-studio)