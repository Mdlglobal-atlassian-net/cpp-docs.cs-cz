---
title: Používání nástroje kreslení
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.drawing
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
- Image editor [C++], drawing lines
- shapes, drawing
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
ms.openlocfilehash: 72224581e021a22b31ec5e6fa5940ff5a568a4e0
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320546"
---
# <a name="using-a-drawing-tool"></a>Používání nástroje kreslení

**Image** uživatele od ruky, vykreslování a mazání nástroje všechny fungují stejně jako editor: Vyberte nástroj a v případě potřeby [vyberte barvy popředí a pozadí](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) a možnosti velikosti a tvaru. Přesuňte ukazatel myši na obrázku a kliknutí nebo tažením nakreslete a vymazat.

Když vyberete **gumy** nástroj, **štětce** nástroje, nebo **rozprašovač** nástroji pro výběr možnosti zobrazí možnosti tohoto nástroje.

> [!TIP]
> Namísto použití **gumy** tool, pravděpodobně pro vás bude pohodlnější kreslete barvu pozadí s jedním z nástrojů pro kreslení.

Můžete zvolit buď z nástrojů pro kreslení **Editor obrázků** nástrojů nebo **Image** nabídky.

## <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Vyberte a použijte nástroj pro vykreslování na panelu nástrojů editoru obrázků

1. Vyberte tlačítko na **Editor obrázků** nástrojů.

   - **Gumy** nástroj barvy bitová kopie se aktuální barvu pozadí při stisknutí levého tlačítka myši.

   - **Tužky** nástroj od ruky nakreslí konstantní šířku jeden pixel.

   - **Výběr možnosti určuje velikost a tvar nástroj štětec**.

   - **Rozprašovač** nástroj náhodně distribuuje barev pixelů kolem středu štětce.

        > [!TIP]
        >  Popisy tlačítek se zobrazí, když ukazatel myši najedete myší na tlačítka na [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md). Následující tipy vám umožní identifikovat konkrétní tlačítka uvedeným.

1. V případě potřeby vyberte barvy a štětce:

   - V [barvy palety](../windows/colors-window-image-editor-for-icons.md), vyberte levé tlačítko myši pro výběr barev popředí nebo na tlačítko pravým tlačítkem myši a vyberte barvu pozadí.

   - V [výběr možnosti](../windows/toolbar-image-editor-for-icons.md), vyberte prosím obrazec představující štětec, který chcete použít.

1. Přejděte na místo na obrázku, kde chcete spustit, kreslení nebo vykreslování. Tvar ukazatele změny podle nástroj, který jste vybrali.

1. Stiskněte klávesu levé tlačítko myši (Barva popředí) nebo pravým tlačítkem myši (pro barvu pozadí) a podržte ho při vykreslení.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Vyberte a používání nástroje kreslení z nabídky Image

1. Vyberte **Image** nabídky a vybereme **nástroje** příkazu.

1. Kaskádové podnabídce zvolte nástroj, který chcete použít.

## <a name="drawing-lines-or-closed-figures"></a>Kreslení čar nebo uzavřených obrázků

Editor obrázků nástrojů pro kreslení čar a uzavřených obrázků všechny fungují stejně jako: Umístěte kurzor na jednom místě a přetáhněte ji do jiného. Pro řádky jsou tyto body koncových bodů. Pro uzavřených obrázků jsou tyto body opačné rohů obdélníku ohraničující na obrázku.

Řádky jsou vykreslovány vedle šířku Určuje aktuální výběr stopy a orámované obrázky jsou vykreslovány vedle šířku Určuje aktuální výběr šířku. Řádky a všechny obrázky, uvedeny i vyplněné, jsou vykreslovány v aktuální barvu popředí při stisknutí levého tlačítka myši, nebo aktuální barvu pozadí při stisknutí pravého tlačítka myši.

### <a name="to-draw-a-line"></a>Chcete-li nakreslit čáru

1. Na [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) (nebo z **Image** nabídce **nástroje** příkaz), zvolte **řádku** nástroj.

1. V případě potřeby vyberte barvy a štětce:

   - V [barvy palety](../windows/colors-window-image-editor-for-icons.md), vyberte levé tlačítko myši pro výběr barev popředí nebo na tlačítko pravým tlačítkem myši a vyberte barvu pozadí.

   - V [výběr možnosti](../windows/toolbar-image-editor-for-icons.md), vyberte prosím obrazec představující štětec, který chcete použít.

1. Umístěte ukazatel myši na řádku počáteční bod.

1. Přetáhněte do koncového bodu čáry.

### <a name="to-draw-a-closed-figure"></a>Chcete-li nakreslit uzavřený útvar

1. Na **Editor obrázků** nástrojů (nebo z **Image** nabídce **nástroje** příkaz), vyberte **kreslení obrázku uzavřeno** nástroj.

   **Kreslení obrázku uzavřeno** nástroje pro vytváření obrázků, jak je uvedeno v jejich příslušných tlačítek.

1. V případě potřeby vyberte barvy a šířku čáry.

1. Přesuňte ukazatel na jeden z rohů obdélníkovou oblast, ve kterém chcete nakreslit obrázek.

1. Přetažením ukazatele šikmo protilehlého rohu.

## <a name="create-a-custom-brush"></a>Vytvoření vlastního štětce

Vlastní štětce je obdélníkovou část bitovou kopii, která sbírání a používat jako jeden z **Image** předem připravená štětce editoru. Všechny operace, které můžete provádět na výběr, můžete provádět na vlastní štětce.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Vytvoření vlastního štětce z část obrázku

1. [Vyberte část obrázku](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) , kterou chcete použít pro štětce.

1. Podržení **Shift** klíče dolů, vyberte ve výběru a proveďte operaci přetažení přes obrázek.

   \- nebo –

1. Z **Image** nabídce zvolte **použít výběr jako štětce**.

   Váš výběr se změní vlastní štětec, který distribuuje barev ve výběru mezi bitovou kopii. Zkopíruje výběr jsou ponechána na cestě přetahování. Tím pomaleji se při přetahování, jsou provedeny další kopie.

   > [!NOTE]
   > Výběr **použít výběr jako štětce** bez nejprve vyberete část obrázku použije celého obrázku jako štětce. Výsledek použití vlastního štětce také závisí na tom, zda jste vybrali [neprůhledné nebo průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Pixelů vlastního štětce, které odpovídají barvě pozadí jsou obvykle transparentní: není vykreslení přes stávající bitovou kopii. Toto chování můžete změnit tak, aby barvu pozadí pixelů vykreslení přes stávající bitovou kopii.

Vlastní štětce jako razítko nebo vzorníku slouží k vytvoření různých speciální efekty.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Pro kreslení tvarů vlastní štětec pozadí barvou

1. [Vyberte neprůhledné nebo průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

1. [Nastavit barvu pozadí](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) barvu, ve kterém chcete kreslit.

1. Pozice vlastního štětce, ve které chcete kreslit.

1. Vyberte pravé tlačítko myši. Jakékoli neprůhledné oblastech vlastního štětce vykresleny barvou pozadí.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Dvakrát nebo polovinu velikost vlastního štětce

Stisknutím klávesy **znaménko Plus** (**+**) klíč na dvojnásobek velikosti štětce nebo **znaménko Minus** (**-**) klíč na polovinu ho .

### <a name="to-cancel-the-custom-brush"></a>Chcete-li zrušit vlastního štětce

Stisknutím klávesy **Esc** nebo zvolte jiný nástroj pro vykreslování.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také:

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)<br/>
[Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)