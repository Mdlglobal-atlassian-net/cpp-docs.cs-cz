---
title: 'Postupy: Použití nástroje kreslení'
ms.date: 02/15/2019
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
ms.openlocfilehash: 7b362749c9a5cb1c7ec77e5cac8625aa7eb260f0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037786"
---
# <a name="how-to-use-a-drawing-tool"></a>Postupy: Použití nástroje kreslení

**Editor obrázků** má kreslení a mazání nástrojů všechny fungují stejně. Vyberte nástroje a v případě potřeby [vyberte barvy popředí a pozadí](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) a možnosti velikosti a tvaru. Přesuňte ukazatel myši na obrázku a kliknutí nebo tažením nakreslete a vymazat.

## <a name="drawing-tools"></a>Nástroje pro kreslení

Můžete zvolit buď z nástrojů pro kreslení **Editor obrázků** nástrojů nebo **Image** nabídky. Když vyberete **gumy** nástroj, **štětce** nástroje, nebo **rozprašovač** nástroji pro výběr možnosti zobrazí možnosti tohoto nástroje.

> [!TIP]
>  Popisy tlačítek se zobrazí, když ukazatel myši najedete myší na tlačítka na [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md). Následující tipy vám umožní identifikovat konkrétní tlačítka uvedeným.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Vyberte a použijte nástroj pro vykreslování na panelu nástrojů editoru obrázků

1. Vyberte tlačítko na **Editor obrázků** nástrojů.

   - **Gumy** nástroj barvy bitová kopie se aktuální barvu pozadí při stisknutí levého tlačítka myši.

      > [!TIP]
      > Namísto použití **gumy** tool, pravděpodobně pro vás bude pohodlnější kreslete barvu pozadí s jedním z nástrojů pro kreslení.

   - **Tužky** nástroj od ruky nakreslí konstantní šířku jeden pixel.

   - **Štětce** nástroj má různých forem a velikostí.

   - **Rozprašovač** nástroj náhodně distribuuje barev pixelů kolem středu štětce.

1. V případě potřeby vyberte barvy a štětce:

   - V [barvy palety](../windows/colors-window-image-editor-for-icons.md), vyberte levé tlačítko myši pro výběr barev popředí nebo na tlačítko pravým tlačítkem myši a vyberte barvu pozadí.

   - V [výběr možnosti](../windows/toolbar-image-editor-for-icons.md), vyberte prosím obrazec představující štětec, který chcete použít.

1. Přejděte na místo na obrázku, kde chcete spustit, kreslení nebo vykreslování. Tvar ukazatele změny podle nástroj, který jste vybrali.

1. Stiskněte klávesu levé tlačítko myši (Barva popředí) nebo pravým tlačítkem myši (pro barvu pozadí) a podržte ho při vykreslení.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Vyberte a používání nástroje kreslení z nabídky Image

1. Přejděte do nabídky **Image** > **nástroje**.

1. Kaskádové podnabídce zvolte nástroj, který chcete použít.

## <a name="lines-or-closed-figures"></a>Čar nebo uzavřených obrázků

**Editor obrázků** nástrojů pro kreslení čar a uzavřených obrázků všechny fungují stejně jako: Umístěte kurzor na jednom místě a přetáhněte ji do jiného. Pro řádky jsou tyto body koncových bodů. Pro uzavřených obrázků jsou tyto body opačné rohů obdélníku ohraničující na obrázku.

Řádky jsou vykreslovány vedle šířku Určuje aktuální výběr stopy a orámované obrázky jsou vykreslovány vedle šířku Určuje aktuální výběr šířku. Řádky a všechny obrázky, uvedeny i vyplněné, jsou vykreslovány v aktuální barvu popředí při stisknutí levého tlačítka myši, nebo aktuální barvu pozadí při stisknutí pravého tlačítka myši.

### <a name="to-draw-a-line"></a>Chcete-li nakreslit čáru

1. Použití [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) nebo přejděte do nabídky **Image**> **nástroje** a zvolte **řádku** nástroj.

1. V případě potřeby vyberte barvy a štětce:

   - V [barvy palety](../windows/colors-window-image-editor-for-icons.md), vyberte levé tlačítko myši pro výběr barev popředí nebo na tlačítko pravým tlačítkem myši a vyberte barvu pozadí.

   - V [výběr možnosti](../windows/toolbar-image-editor-for-icons.md), vyberte prosím obrazec představující štětec, který chcete použít.

1. Umístěte ukazatel myši na řádku počáteční bod.

1. Přetáhněte do koncového bodu čáry.

### <a name="to-draw-a-closed-figure"></a>Chcete-li nakreslit uzavřený útvar

1. Použití **Editor obrázků** nástrojů nebo přejděte do nabídky **Image** > **nástroje** a vyberte **kreslení obrázku uzavřeno** nástroj.

   **Kreslení obrázku uzavřeno** nástroje pro vytváření obrázků, jak je uvedeno v jejich příslušných tlačítek.

1. V případě potřeby vyberte barvy a šířku čáry.

1. Přesuňte ukazatel na jeden z rohů obdélníkovou oblast, ve kterém chcete nakreslit obrázek.

1. Přetažením ukazatele šikmo protilehlého rohu.

## <a name="custom-brushes"></a>Vlastní štětce

Vlastní štětce je obdélníkovou část bitovou kopii, která sbírání a používat jako jeden z **Editor obrázků**pro předem připravená stopy. Všechny operace, které můžete provádět na výběr, můžete provádět na vlastní štětce.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Vytvoření vlastního štětce z část obrázku

1. Vyberte část obrázku, který chcete použít pro štětce.

1. Uložení **Shift** klíče dolů, vyberte ve výběru a proveďte operaci přetažení přes obrázek nebo přejděte do nabídky **Image** > **použít výběr jako štětce**.

   Váš výběr se změní vlastní štětec, který distribuuje barev ve výběru mezi bitovou kopii. Zkopíruje výběr jsou ponechána na cestě přetahování. Tím pomaleji se při přetahování, jsou provedeny další kopie.

   > [!NOTE]
   > Výběr **použít výběr jako štětce** bez nejprve vyberete část obrázku použije celého obrázku jako štětce. Výsledek použití vlastního štětce také závisí na tom, zda jste vybrali [neprůhledné nebo průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Pixelů vlastního štětce, které odpovídají barvě pozadí jsou obvykle transparentní: není vykreslení přes stávající bitovou kopii. Toto chování můžete změnit tak, aby barvu pozadí pixelů vykreslení přes stávající bitovou kopii.

Vlastní štětce jako razítko nebo vzorníku slouží k vytvoření různých speciální efekty.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Pro kreslení tvarů vlastní štětec pozadí barvou

1. Vyberte neprůhledné nebo průhledné pozadí.

1. Nastavte barvu pozadí na barvu, ve kterém chcete kreslit.

1. Pozice vlastního štětce, ve které chcete kreslit.

1. Vyberte pravé tlačítko myši. Jakékoli neprůhledné oblastech vlastního štětce vykresleny barvou pozadí.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Dvakrát nebo polovinu velikost vlastního štětce

Stisknutím klávesy **znaménko Plus** (**+**) klíč na dvojnásobek velikosti štětce nebo **znaménko Minus** (**-**) klíč na polovinu ho .

### <a name="to-cancel-the-custom-brush"></a>Chcete-li zrušit vlastního štětce

Stisknutím klávesy **Esc** nebo zvolte jiný nástroj pro vykreslování.

## <a name="requirements"></a>Požadavky

Žádný

## <a name="see-also"></a>Viz také:

[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)<br/>
[Postupy: Vytvoření ikony nebo jiného obrázku](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Postupy: Úprava obrázku](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Postupy: Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>