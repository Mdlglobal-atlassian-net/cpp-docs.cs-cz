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
ms.openlocfilehash: 8f33ef6d0198f083e7cf1b1e1dc2129be9b3fab4
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320559"
---
# <a name="string-editor-c"></a>Editor řetězců (C++)

Tabulka řetězců je prostředek Windows, který obsahuje seznam ID, hodnoty a popisky pro všechny řetězce vaší aplikace. Například výzvy stavový řádek jsou umístěny v tabulce řetězců.

Při vývoji aplikace, máte několik tabulek řetězců, jeden pro každý jazyk nebo podmínku. Spustitelný soubor modulu má však pouze jedna tabulka řetězců. Běžící aplikaci může odkazovat několik tabulek řetězců, pokud vložené tabulky do jiné knihovny DLL.

Tabulky řetězců umožňují snadno lokalizovat vaši aplikaci do různých jazyků. Pokud jsou všechny řetězce v tabulce řetězců, je možné lokalizovat aplikaci při převodu řetězce (a další prostředky) bez změny zdrojového kódu. Tato situace je lepší než ručně vyhledávání a nahrazování různých řetězců ve zdrojových souborech.

## <a name="how-to"></a>Postupy

Použití **řetězec** editor pro následující akce:

### <a name="to-find-a-string-resource-in-the-string-table"></a>Chcete-li nalézt zdroj řetězce v tabulce řetězců

Můžete vyhledat jeden nebo více řetězců v tabulce řetězců a použít [regulární výrazy](/visualstudio/ide/using-regular-expressions-in-visual-studio) s **najít v souborech** příkazu (**upravit** nabídky) najít všechny instance řetězce které odpovídají vzoru.

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](../windows/resource-view-window.md).

1. Na **upravit** nabídce vyberte možnost **najít a nahradit**, klikněte na tlačítko **najít**.

1. V **najít** pole, vyberte předchozí hledaný řetězec z rozevíracího seznamu nebo zadejte titulek identifikátor textu nebo prostředku řetězce, které chcete najít.

1. Vyberte některou z **najít** možnosti.

1. Vyberte **najít další**.

   > [!TIP]
   > Chcete-li použít regulární výrazy při vyhledávání souborů, použijte **najít v souborech** příkazu. Zadejte regulární výraz k vyhledání vzoru, nebo vyberte tlačítko vpravo od **najít** pole k zobrazení seznamu hledání regulárních výrazů. Když vyberete výrazu z tohoto seznamu, je nahrazen jako hledaný text v **najít** pole. Pokud používáte regulární výrazy, ujistěte se, **použít: Regulární výrazy** je zaškrtnuto políčko.

### <a name="to-add-or-delete-a-string-resource"></a>Přidat nebo odstranit prostředek řetězce

Můžete rychle vložení nebo odstranění položek do řetězce pomocí tabulky **řetězec** editoru. Nové řetězce jsou umístěny na konci v tabulce a jsou uvedeny další k dispozici identifikátor. Potom můžete upravit **ID**, **hodnotu**, nebo **titulek** vlastnosti v [okno vlastností](/visualstudio/ide/reference/properties-window) podle potřeby.

**Řetězec** editor zajišťuje nepoužíváte ID, které se už používá. Pokud vyberete ID už používá, **řetězec** oznámíme vám to a zařaďte obecné jedinečné ID, například editor `IDS_STRING58113`.

#### <a name="to-add-a-string-table-entry"></a>Přidání položky tabulky řetězců

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](../windows/resource-view-window.md).

1. Klikněte pravým tlačítkem v rámci tabulky řetězců a zvolte **nový řetězec** z místní nabídky.

1. V **řetězec** editoru, vyberte možnost **ID** z rozevíracího seznamu ID nebo typ ID přímo v místě.

1. Upravit **hodnota**, v případě potřeby.

1. Zadejte položku pro **titulek**.

   > [!NOTE]
   > Řetězce s hodnotou Null nejsou povoleny v tabulkách řetězců Windows. Pokud vytvoříte položku v tabulce řetězec, který je prázdný řetězec, zobrazí se zpráva s výzvou k "Prosím zadejte řetězec pro tuto položku tabulky."

#### <a name="to-delete-a-string-table-entry"></a>Chcete-li odstranit položky tabulky řetězců

Vyberte položku, kterou chcete odstranit. Udělejte jednu z následujících akcí:

- Na **upravit** nabídce vyberte možnost **odstranit**.

- Klikněte pravým tlačítkem na řetězec, který chcete odstranit a zvolit **odstranit** z místní nabídky.

- Stisknutím klávesy **odstranit** klíč.

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Přesunutí řetězce z jednoho zdrojového souboru skriptu na jiný

1. V obou souborů RC otevřete tabulky řetězců. (Další informace najdete v tématu [zobrazování prostředků v prostředků skriptu souboru mimo of projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).)

1. Klikněte pravým tlačítkem na řetězec, který chcete přesunout a zvolte **Vyjmout** z místní nabídky.

1. Umístěte kurzor na cíli **Editor řetězců** okna.

1. V souboru .rc, do kterého chcete přesunout řetězec, klikněte pravým tlačítkem a zvolte **vložit** z místní nabídky.

   > [!NOTE]
   > Pokud **ID** nebo **hodnotu** přesunutý řetězec konfliktů s existujícím **ID** nebo **hodnotu** v cílovém souboru a buď **ID** nebo **hodnotu** změn přesunutý řetězec. Pokud řetězec existuje se stejným **ID**, **ID** změn přesunutý řetězec. Pokud řetězec existuje se stejným **hodnotu**, **hodnotu** změn přesunutý řetězec.

### <a name="to-change-the-properties-of-a-string-resource"></a>Chcete-li změnit vlastnosti prostředku řetězce

Chcete-li změnit ID, hodnotu a popisek vlastnosti můžete použít místní úpravy.

#### <a name="to-change-a-string-or-its-identifier"></a>Chcete-li změnit její identifikátor nebo řetězec

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](../windows/resource-view-window.md).

1. Vyberte řetězec, který chcete upravit a dvakrát klikněte **ID**, **hodnotu**, nebo **titulek** sloupce. Nyní můžete:

   - Vyberte **ID** z **rozevírací seznam ID** seznamu nebo typu `ID` přímo na místě.

   - Zadejte jiné číslo v **hodnotu** sloupce.

   - Zadejte úpravy v operaci **titulek** sloupce.

        > [!NOTE]
        >  Můžete také upravit vlastnosti řetězce v [okno vlastností](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Změna vlastnosti titulku více řetězcové prostředky

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](../windows/resource-view-window.md).

1. Vyberte řetězců, které chcete změnit současným **Ctrl** klíče při výběru každé z nich.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), zadejte novou hodnotu pro vlastnost, kterou chcete změnit.

1. Stisknutím klávesy **zadejte**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Přidání formátovacích nebo speciálních znaků do řetězce prostředků

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](../windows/resource-view-window.md).

1. Vyberte řetězec, který chcete upravit.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), přidejte všechny standardní řídicí sekvence, které tady textu **titulek** pole a stiskněte klávesu **Enter**.

   |Chcete-li získat tento|Zadejte toto|
   |-----------------|---------------|
   | Nový řádek | \\n |
   | Návrat na začátek řádku | \\r |
   | Karta | \\t |
   | Zpětné lomítko (\\) | \\\\ |
   | Znak ASCII | \\ddd (osmičkové soustavě) |
   | upozornění (zvonek) | \\a |

> [!NOTE]
> **Řetězec** editor nepodporuje kompletní řídicí znaky ASCII. Můžete použít pouze ty uvedené výše.

> [!NOTE]
> Windows neumožňuje vytvoření tabulky prázdný řetězec. Pokud vytvoříte tabulku řetězců s žádné položky, odstraní se automaticky při ukládání souboru prostředků.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)<br/>
[Řetězce](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[O řetězcích](/windows/desktop/menurc/about-strings)<br/>
[Přizpůsobení rozložení oken](/visualstudio/ide/customizing-window-layouts-in-visual-studio)