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
ms.openlocfilehash: bea53c33ef723cf8c98d0c542d24389e730c092a
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563300"
---
# <a name="string-editor-c"></a>Editor řetězců (C++)

Tabulka řetězců je prostředek Windows, který obsahuje seznam ID, hodnoty a popisky pro všechny řetězce vaší aplikace. Například výzvy stavový řádek jsou umístěny v tabulce řetězců.

Při vývoji aplikace, máte několik tabulek řetězců, jeden pro každý jazyk nebo podmínku. Spustitelný soubor modulu má však pouze jedna tabulka řetězců. Běžící aplikaci může odkazovat několik tabulek řetězců, pokud vložené tabulky do jiné knihovny DLL.

Tabulky řetězců umožňují snadno lokalizovat vaši aplikaci do různých jazyků. Pokud jsou všechny řetězce v tabulce řetězců, je možné lokalizovat aplikaci při převodu řetězce (a další prostředky) bez změny zdrojového kódu. Tato situace je lepší než ručně vyhledávání a nahrazování různých řetězců ve zdrojových souborech.

> [!NOTE]
> Windows neumožňuje vytvoření tabulky prázdný řetězec. Pokud vytvoříte tabulku řetězců s žádné položky, odstraní se automaticky při ukládání souboru prostředků.

## <a name="how-to"></a>Postupy

**Editor řetězců** vám umožní:

### <a name="to-find-a-string-resource-in-the-string-table"></a>Chcete-li nalézt zdroj řetězce v tabulce řetězců

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](/windows/how-to-create-a-resource-script-file#create-resources).

1. Přejděte do nabídky **upravit** > **najít a nahradit** a zvolte **najít**.

1. V **najít** pole, vyberte předchozí hledaný řetězec z rozevíracího seznamu nebo zadejte titulek identifikátor textu nebo prostředku řetězce, které chcete najít.

1. Vyberte některou z **najít** možnosti a vyberte **najít další**.

> [!TIP]
> Použití [regulární výrazy](/visualstudio/ide/using-regular-expressions-in-visual-studio) při vyhledávání souborů, použijte **najít v souborech** v příkaz **upravit** nabídky.
>
> Zadejte regulární výraz k vyhledání vzoru, nebo vyberte tlačítko vpravo od **najít** pole k zobrazení seznamu hledání regulárních výrazů. Když vyberete výrazu z tohoto seznamu, je nahrazen jako hledaný text v **najít** pole.
>
> Pokud používáte regulární výrazy, ujistěte se, **použít: Regulární výrazy** je zaškrtnuto políčko.

### <a name="to-add-or-delete-a-string-resource"></a>Přidat nebo odstranit prostředek řetězce

Můžete rychle vložení nebo odstranění položek do řetězce pomocí tabulky **Editor řetězců**. Nové řetězce jsou umístěny na konci v tabulce a jsou uvedeny další k dispozici identifikátor. Můžete upravit **ID**, **hodnotu**, nebo **titulek** vlastnosti [okno vlastností](/visualstudio/ide/reference/properties-window) podle potřeby.

**Editor řetězců** zajišťuje, nepoužívejte ID, které se už používá. Pokud vyberete ID už používá, **Editor řetězců** oznámíme vám to a zařaďte obecné jedinečné ID, například `IDS_STRING58113`.

#### <a name="to-add-a-string-table-entry"></a>Přidání položky tabulky řetězců

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](/windows/how-to-create-a-resource-script-file#create-resources).

1. Klikněte pravým tlačítkem v rámci tabulky řetězců a zvolte **nový řetězec**.

1. V **Editor řetězců**vyberte **ID** z **ID** rozevíracího seznamu nebo typ *ID* přímo na místě.

1. Upravit **hodnota**, v případě potřeby.

1. Zadejte položku pro **titulek**.

   > [!NOTE]
   > Řetězce s hodnotou Null nejsou povoleny v tabulkách řetězců Windows. Pokud vytvoříte položku v tabulce řetězec, který je řetězec s hodnotou null, obdržíte zprávu s výzvou k **zadejte řetězec pro tuto položku tabulky**.

#### <a name="to-delete-a-string-table-entry"></a>Chcete-li odstranit položky tabulky řetězců

Vyberte položku, kterou chcete odstranit a proveďte jednu z následujících akcí:

- Přejděte do nabídky **upravit** > **odstranit**.

- Klikněte pravým tlačítkem na řetězec, který chcete odstranit a zvolte **odstranit**.

- Stisknutím klávesy **odstranit** klíč.

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Přesunutí řetězce z jednoho zdrojového souboru skriptu na jiný

1. [Otevřete tabulky řetězců v obou souborech .rc](../windows/how-to-create-a-resource-script-file.md).

1. Klikněte pravým tlačítkem na řetězec, který má přesunout a zvolte **Vyjmout**.

1. Umístěte kurzor na cíli **Editor řetězců** okna.

1. V *.rc* souboru, do kterého chcete přesunout řetězec, klikněte pravým tlačítkem myši a zvolte **vložit**.

> [!NOTE]
> Pokud **ID** nebo **hodnotu** přesunutý řetězec konfliktů s existujícím **ID** nebo **hodnotu** v cílovém souboru a buď tento **ID** nebo **hodnotu** změn přesunutý řetězec.

### <a name="to-change-the-properties-of-a-string-resource"></a>Chcete-li změnit vlastnosti prostředku řetězce

Můžete použít místní úpravy. Chcete-li změnit **ID**, **hodnotu**, a **titulek** vlastnosti.

> [!NOTE]
>  Můžete také upravit vlastnosti řetězce v [okno vlastností](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-a-string-or-its-identifier"></a>Chcete-li změnit její identifikátor nebo řetězec

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](/windows/how-to-create-a-resource-script-file#create-resources).

1. Vyberte řetězec, který chcete upravit a dvakrát klikněte **ID**, **hodnotu**, nebo **titulek** sloupec a pak můžete:

   - Vyberte **ID** z **ID** rozevíracího seznamu nebo typ *ID* přímo na místě.

   - Zadejte jiné číslo v **hodnotu** sloupce.

   - Zadejte úpravy v operaci **titulek** sloupce.

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Změna vlastnosti titulku více řetězcové prostředky

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](/windows/how-to-create-a-resource-script-file#create-resources).

1. Vyberte řetězců, které chcete změnit současným **Ctrl** klíče při výběru každé z nich.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), zadejte novou hodnotu pro vlastnost, kterou chcete změnit.

1. Stisknutím klávesy **zadejte**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Přidání formátovacích nebo speciálních znaků do řetězce prostředků

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](/windows/how-to-create-a-resource-script-file#create-resources).

1. Vyberte řetězec, který chcete upravit.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), přidejte všechny standardní řídicí sekvence, které tady textu **titulek** pole a stiskněte klávesu **Enter**.

   |Chcete-li získat to...|Zadejte toto...|
   |-----------------|---------------|
   | Nový řádek | \\n |
   | Návrat na začátek řádku | \\r |
   | Karta | \\t |
   | Zpětné lomítko (\\) | \\\\ |
   | Znak ASCII | \\ddd (osmičkové soustavě) |
   | upozornění (zvonek) | \\a |

   > [!NOTE]
   > **Editor řetězců** nepodporuje kompletní řídicí znaky ASCII. Můžete použít pouze ty uvedené výše.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)
<!--
[Strings](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[About Strings](/windows/desktop/menurc/about-strings)<br/>
[Customizing window layouts](/visualstudio/ide/customizing-window-layouts-in-visual-studio)-->