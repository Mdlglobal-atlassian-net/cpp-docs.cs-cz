---
title: 'Postup: Použití kreslicího nástroje'
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
ms.openlocfilehash: b0041124c35414a0c1c998642b5321319602c872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359857"
---
# <a name="how-to-use-a-drawing-tool"></a>Postup: Použití kreslicího nástroje

**Editor obrázků** má nástroje pro kreslení a vymazání od ruky, které všechny fungují stejným způsobem. Vyberete nástroj a v případě potřeby [vyberete barvy popředí a pozadí](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) a volby velikosti a tvaru. Poté přesuňte ukazatel na obrázek a klepnutím nebo tažením nakreslete a smažete.

## <a name="drawing-tools"></a>Nástroje pro kreslení

Kreslicí nástroje můžete vybrat buď z panelu nástrojů **Editor obrázků,** nebo z nabídky **Obraz.** Když vyberete nástroj **eráž,** **nástroj štětec** nebo nástroj **rozprašovač,** volič voleb zobrazí volby tohoto nástroje.

> [!TIP]
> Tipy nástrojů se zobrazí, když najedete kurzorem na tlačítka na [panelu nástrojů Editor obrázků](../windows/toolbar-image-editor-for-icons.md). Tyto tipy vám pomohou identifikovat konkrétní zde uvedená tlačítka.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Výběr a použití kreslicího nástroje z panelu nástrojů Editor obrázků

1. Vyberte tlačítko na panelu nástrojů **Editor obrázků.**

   - Nástroj **eraser** maluje obraz aktuální barvou pozadí, když stisknete levé tlačítko myši.

      > [!TIP]
      > Namísto použití nástroje **eraser** může být vhodnější kreslit barvu pozadí jedním z kreslicích nástrojů.

   - Nástroj **tužka** kreslí od ruky v konstantní šířce jednoho pixelu.

   - Nástroj **štětec** má různé tvary a velikosti.

   - Nástroj **rozprašovač** náhodně rozmístí barevné obrazové body kolem středu stopy.

1. V případě potřeby vyberte barvy a štětec:

   - V [paletě Barvy](../windows/colors-window-image-editor-for-icons.md)vyberte levé tlačítko myši a vyberte barvu popředí nebo pravé tlačítko myši a vyberte barvu pozadí.

   - Ve [voliči voleb](../windows/toolbar-image-editor-for-icons.md)vyberte obrazec představující stopu, kterou chcete použít.

1. Najedujte na místo na obrázku, kde chcete začít kreslit nebo malovat. Ukazatel změní tvar podle vybraného nástroje.

1. Stiskněte levé tlačítko myši (pro barvu popředí) nebo pravé tlačítko myši (pro barvu pozadí) a podržte ho při kreslení.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Výběr a použití kreslicího nástroje z nabídky Obraz

1. Přejděte do nabídky **Nástroje obrázku** > **Tools**.

1. V podnabídce kaskádové zvolte nástroj, který chcete použít.

## <a name="lines-or-closed-figures"></a>Čáry nebo uzavřené obrázky

Nástroje **Editor obrázků** pro kreslení čar a uzavřených obrázků fungují stejným způsobem: umístěte textový kurzor na jeden bod a táhněte do jiného. Pro čáry jsou tyto body koncovými body. U uzavřených čísel jsou tyto body protilehlými rohy obdélníku ohraničujícího obrázek.

Čáry jsou nakresleny v šířce určené aktuálním výběrem stopy a rámečkované obrázky jsou nakresleny v šířce určené výběrem aktuální šířky. Čáry a všechny obrázky, jak zarámované, tak vyplněné, jsou nakresleny v aktuální barvě popředí, pokud stisknete levé tlačítko myši, nebo v aktuální barvě pozadí, pokud stisknete pravé tlačítko myši.

### <a name="to-draw-a-line"></a>Nakreslení čáry

1. Použijte [panel nástrojů Editor obrázků](../windows/toolbar-image-editor-for-icons.md) nebo přejděte do nabídky **Nástroje obrazu**> **Tools** a zvolte nástroj **čára.**

1. V případě potřeby vyberte barvy a štětec:

   - V [paletě Barvy](../windows/colors-window-image-editor-for-icons.md)vyberte levé tlačítko myši a vyberte barvu popředí nebo pravé tlačítko myši a vyberte barvu pozadí.

   - Ve [voliči voleb](../windows/toolbar-image-editor-for-icons.md)vyberte obrazec představující stopu, kterou chcete použít.

1. Umístěte ukazatel na počáteční bod čáry.

1. Přetáhněte do koncového bodu čáry.

### <a name="to-draw-a-closed-figure"></a>Nakreslení uzavřeného obrázku

1. Použijte panel nástrojů **Editor obrázků** nebo přejděte do nabídky **Nástroje** > **obrazu** a vyberte nástroj **kreslení s uzavřeným obrázkem.**

   Nástroje **kreslení s uzavřeným obrázkem** vytvářejí obrázky, jak je uvedeno na příslušných tlačítkách.

1. V případě potřeby vyberte barvy a šířku čáry.

1. Přesuňte ukazatel do jednoho rohu obdélníkové oblasti, ve které chcete obrázek nakreslit.

1. Přetáhněte ukazatel do diagonálně protilehlého rohu.

## <a name="custom-brushes"></a>Vlastní stopy štětců

Vlastní stopa je obdélníková část obrázku, kterou zvednete a používáte jako jeden z hotových štětců **editoru obrázků.** Všechny operace, které můžete provádět s výběrem, můžete provádět také na vlastní stopě.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Vytvoření vlastní stopy z části obrazu

1. Vyberte část obrazu, kterou chcete použít pro stopu.

1. Podržte klávesu **Shift** stisknutou, zvolte ve výběru a přetáhněte ji přes obraz nebo přejděte do nabídky **Použít** > **výběr jako štětec**.

   Výběr se stane vlastní stopou, která rozmístí barvy ve výběru přes obraz. Kopie výběru jsou ponechány podél táhlé cesty. Čím pomaleji táhnete, tím více kopií se zhotovuje.

   > [!NOTE]
   > Když vyberete možnost **Použít výběr jako stopu** bez předchozího výběru části obrazu, použijese celý obraz jako stopa. Výsledek použití vlastní stopy bude také záviset na tom, zda jste vybrali [neprůhledné nebo průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Obrazové body ve vlastní stopě, které odpovídají aktuální barvě pozadí, jsou obvykle průhledné: nemalují přes existující obraz. Toto chování můžete změnit tak, aby obrazové body barvy pozadí překreslovat přes existující obraz.

Vlastní stopu můžete použít jako razítko nebo vzorník k vytvoření různých speciálních efektů.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Kreslení vlastních tvarů stopy v barvě pozadí

1. Vyberte neprůhledné nebo průhledné pozadí.

1. Nastavte barvu pozadí na barvu, ve které chcete kreslit.

1. Umístěte vlastní štětec na místo, kam chcete kreslit.

1. Vyberte pravé tlačítko myši. Všechny neprůhledné oblasti vlastní stopy jsou nakresleny v barvě pozadí.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Zdvojnásobení nebo snížení vlastní velikosti stopy na polovinu

Stisknutím klávesy**+** **Znaménko plus** ( ) zdvojnásobte velikost stopy nebo klávesou **Znaménko mínus** (**-**) ji rozpůlte na polovinu.

### <a name="to-cancel-the-custom-brush"></a>Zrušení vlastní stopy

Stiskněte **Esc** nebo zvolte jiný kreslicí nástroj.

## <a name="requirements"></a>Požadavky

Žádný

## <a name="see-also"></a>Viz také

[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)<br/>
[Postup: Vytvoření ikony nebo jiného obrázku](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Postup: Úprava obrázku](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Postup: Práce s barvami](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
