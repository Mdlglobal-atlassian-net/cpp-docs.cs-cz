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
ms.openlocfilehash: b0fb077752cf1912e07175c68cdc8acfe758b0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370244"
---
# <a name="string-editor-c"></a>Editor řetězců (C++)

Tabulka řetězců je prostředek systému Windows, který obsahuje seznam ID, hodnot a titulků pro všechny řetězce aplikace. Například výzvy stavového řádku jsou umístěny v tabulce řetězců.

Při vývoji aplikace můžete mít několik řetězcových tabulek – jednu pro každý jazyk nebo podmínku. Spustitelný modul má však pouze jednu tabulku řetězců. Spuštěná aplikace může odkazovat na několik tabulek řetězců, pokud tabulky vložíte do různých knihoven DLL.

Řetězce tabulky usnadňují lokalizaci aplikace do různých jazyků. Pokud jsou všechny řetězce v tabulce řetězců, můžete lokalizovat aplikaci překladem řetězců (a dalších prostředků) bez změny zdrojového kódu. Tato situace je více žádoucí než ruční hledání a nahrazení různých řetězců ve zdrojových souborech.

> [!NOTE]
> Systém Windows neumožňuje vytváření prázdných tabulek řetězců. Pokud vytvoříte tabulku řetězců bez položek, bude při uložení souboru prostředků automaticky odstraněna.

## <a name="how-to"></a>Postup

**Editor řetězců** umožňuje:

### <a name="to-find-a-string-resource-in-the-string-table"></a>Vyhledání řetězcového prostředku v tabulce řetězců

1. Otevřete tabulku řetězců poklepáním na její ikonu v [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources).

1. Přejděte do nabídky **Upravit** > **a nahradit** a zvolte **Najít**.

1. Do pole **Najít** vyberte předchozí hledaný řetězec z rozevíracího seznamu nebo zadejte text titulku nebo identifikátor prostředku řetězce, který chcete najít.

1. Vyberte některou z možností **Najít** a vyberte **Najít další**.

> [!TIP]
> Chcete-li při hledání souborů používat [regulární výrazy,](/visualstudio/ide/using-regular-expressions-in-visual-studio) použijte příkaz **Najít v souborech** v nabídce **Úpravy.**
>
> Zadejte regulární výraz tak, aby odpovídal vzoru, nebo vyberte tlačítko vpravo od pole **Najít,** chcete-li zobrazit seznam výrazů regulárního vyhledávání. Když vyberete výraz z tohoto seznamu, nahradí se jako hledaný text v poli **Najít.**
>
> Pokud používáte regulární výrazy, ujistěte se, že je zaškrtnuté políčko **Použít: Regulární výrazy.**

### <a name="to-add-or-delete-a-string-resource"></a>Přidání nebo odstranění řetězcového prostředku

Položky do tabulky řetězců můžete rychle vložit nebo odstranit pomocí **Editoru řetězců**. Nové řetězce jsou umístěny na konci tabulky a jsou uvedeny další dostupný identifikátor. Vlastnosti **ID**, **Hodnota**nebo **Titulek** můžete podle potřeby upravit v [okně Vlastnosti.](/visualstudio/ide/reference/properties-window)

**Editor řetězců** zajišťuje, že nepoužíváte ID, které je již používáno. Pokud vyberete Již využívaný Identifikátor, **editor řetězců** vás upozorní a `IDS_STRING58113`pak přiřadí obecné jedinečné ID, například .

#### <a name="to-add-a-string-table-entry"></a>Přidání položky tabulky řetězce

1. Otevřete tabulku řetězců poklepáním na její ikonu v [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources).

1. Klepněte pravým tlačítkem myši v tabulce řetězců a zvolte **Nový řetězec**.

1. V **Editoru řetězců**vyberte **ID** z rozevíracího seznamu **ID** nebo zadejte *ID* přímo na místě.

1. V případě potřeby upravte **hodnotu**.

1. Zadejte položku **pro titulek**.

   > [!NOTE]
   > V tabulkách řetězců Windows nejsou povoleny nulové řetězce. Pokud vytvoříte položku v tabulce řetězců, která je nulovým řetězcem, zobrazí se zpráva s **žádostí O zadání řetězce pro tuto položku tabulky**.

#### <a name="to-delete-a-string-table-entry"></a>Odstranění položky tabulky řetězců

Vyberte položku, kterou chcete odstranit, a proveďte jednu z následujících akcí:

- Přejděte do nabídky **Upravit** > **odstranit**.

- Chcete-li odstranit, klepněte pravým tlačítkem myši na řetězec a zvolte **Odstranit**.

- Stiskněte klávesu **Delete.**

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Přesunutí řetězce z jednoho souboru skriptu prostředku do jiného

1. [Otevřete tabulky řetězců v obou souborech RC](../windows/how-to-create-a-resource-script-file.md).

1. Chcete-li řetězec přesunout, klepněte pravým tlačítkem myši a zvolte **Vyjmout**.

1. Umístěte kurzor do okna cílového **editoru řetězců.**

1. V souboru *RC,* do kterého chcete řetězec přesunout, klepněte pravým tlačítkem myši a zvolte **Vložit**.

> [!NOTE]
> Pokud **id** nebo **hodnota** přesunutého řetězce je v konfliktu s existujícím **ID** nebo **hodnotou** v cílovém souboru, změní se toto **ID** nebo **Hodnota** přesunutého řetězce.

### <a name="to-change-the-properties-of-a-string-resource"></a>Změna vlastností řetězcového prostředku

Pomocí úprav na místě můžete změnit vlastnosti **ID**, **Hodnota**a **Titulek.**

> [!NOTE]
> Vlastnosti řetězce můžete také upravit v [okně Vlastnosti](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-a-string-or-its-identifier"></a>Změna řetězce nebo jeho identifikátoru

1. Otevřete tabulku řetězců poklepáním na její ikonu v [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources).

1. Vyberte řetězec, který chcete upravit, a poklepejte na sloupec **ID**, **Hodnota**nebo **Titulek,** pak můžete:

   - V rozevíracím seznamu **ID** vyberte **ID** nebo zadejte *ID* přímo na místo.

   - Do sloupce **Hodnota** zadejte jiné číslo.

   - Do sloupce **Titulek** zadejte úpravy.

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Změna vlastnosti titulku více řetězcových prostředků

1. Otevřete tabulku řetězců poklepáním na její ikonu v [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources).

1. Vyberte řetězce, které chcete změnit, podržením klávesy **Ctrl** při výběru každého z nich.

1. V [okně Vlastnosti](/visualstudio/ide/reference/properties-window)zadejte novou hodnotu vlastnosti, kterou chcete změnit.

1. Stiskněte **Enter**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Přidání formátování nebo speciálních znaků do řetězcového prostředku

1. Otevřete tabulku řetězců poklepáním na její ikonu v [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources).

1. Vyberte řetězec, který chcete upravit.

1. V [okně Vlastnosti](/visualstudio/ide/reference/properties-window)přidejte do textu v poli **Titulek** všechny standardní sekvence escape uvedené níže a stiskněte **Enter**.

   |Chcete-li si to ...|Zadejte toto...|
   |-----------------|---------------|
   | Nový řádek | \\N |
   | Návrat na začátek řádku | \\R |
   | Karta | \\t |
   | Zpětné lomítko (\\) | \\\\ |
   | Znak ASCII | \\ddd (osmičkový zápis) |
   | Výstraha (zvonek) | \\A |

   > [!NOTE]
   > **Editor řetězců** nepodporuje úplnou sadu uvozených znaků ASCI. Můžete použít pouze ty, které jsou uvedeny výše.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Resource Editors](../windows/resource-editors.md)
[Řetězce](/windows/win32/menurc/strings) editorů prostředků<br/>
[O řetězecích](/windows/win32/menurc/about-strings)<br/>
[Přizpůsobení rozložení oken](/visualstudio/ide/customizing-window-layouts-in-visual-studio)
