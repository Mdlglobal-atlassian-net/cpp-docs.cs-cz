---
title: 'Postupy: použití nástroje pro kreslení'
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
ms.openlocfilehash: 61c06ee3fecac18fb95663c0d13474b8bd3b94f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214380"
---
# <a name="how-to-use-a-drawing-tool"></a>Postupy: použití nástroje pro kreslení

**Editor obrázků** má kreslení od ruky a mazání nástrojů, které fungují stejným způsobem. Vyberte nástroj a v případě potřeby [Vyberte barvy popředí a pozadí](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) a možnosti velikosti a tvaru. Pak přesunete ukazatel na obrázek a kliknete nebo táhnete pro kreslení a mazání.

## <a name="drawing-tools"></a>Nástroje pro kreslení

Kreslicí nástroje můžete vybrat buď z panelu nástrojů **editoru obrázků** , nebo z nabídky **Obrázek** . Když vyberete nástroj pro **mazání** , nástroj **štětec** nebo nástroj **rozprašovač** , zobrazí selektor možností tyto možnosti nástroje.

> [!TIP]
>  Když najedete kurzorem na tlačítka na [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md), zobrazí se popisy tlačítek. Tyto tipy vám pomůžou identifikovat konkrétní tlačítka, která jsou tady uvedená.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Výběr a použití nástroje pro kreslení z panelu nástrojů Editor obrázků

1. Vyberte tlačítko na panelu nástrojů **editoru obrázků** .

   - Nástroj **Guma** maluje při stisknutí levého tlačítka myši na obrázek s aktuální barvou pozadí.

      > [!TIP]
      > Místo použití nástroje pro **mazání** je možné, že je snazší kreslit na pozadí pomocí jednoho z nástrojů pro kreslení.

   - Nástroj **Tužka** kreslí FreeHand v konstantní šířce v jednom pixelu.

   - Nástroj **štětec** má různé tvary a velikosti.

   - Nástroj **rozprašovač** náhodně distribuuje barvy pixelů kolem středu štětce.

1. V případě potřeby vyberte barvy a štětec:

   - V [paletě barvy](../windows/colors-window-image-editor-for-icons.md)vyberte levé tlačítko myši a vyberte barvu popředí nebo pravé tlačítko myši a vyberte barvu pozadí.

   - V [selektoru možností](../windows/toolbar-image-editor-for-icons.md)vyberte tvar představující štětec, který chcete použít.

1. Umístěte ukazatel na místo na obrázku, kde chcete spustit kreslení nebo malování. Ukazatel se změní na obrazec podle vybraného nástroje.

1. Stiskněte levé tlačítko myši (pro barvu popředí) nebo pravé tlačítko myši (pro barvu pozadí) a při kreslení ho držte.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Výběr a použití nástroje pro kreslení v nabídce obrázek

1. Přejít na **Image** nabídky > **nástroje**

1. V podnabídce kaskádová nabídka vyberte nástroj, který chcete použít.

## <a name="lines-or-closed-figures"></a>Řádky nebo uzavřené hodnoty

Nástroje **editoru obrázků** pro kreslení čar a uzavřených obrázků fungují stejným způsobem: Umístěte kurzor na jeden bod a přetáhněte ho na jiný. Pro řádky jsou tyto body koncovými body. Pro uzavřené hodnoty jsou tyto body protilehlé rohy obdélníku ohraničujícího obrázek.

Řádky jsou vykresleny na šířku určené pomocí aktuálního výběru štětce a obrázky s rámečkem jsou vykresleny na šířku určené výběrem aktuální šířky. Při stisknutí pravého tlačítka myši nebo při stisknutí pravého tlačítka myši se v aktuální barvě popředí vykreslí řádky a všechny hodnoty, které jsou v rámečcích i vyplněné.

### <a name="to-draw-a-line"></a>Vykreslení čáry

1. Použijte [panel nástrojů Editor obrázků](../windows/toolbar-image-editor-for-icons.md) nebo přejděte na **Image** nabídky> **nástroje** a vyberte nástroj **čára** .

1. V případě potřeby vyberte barvy a štětec:

   - V [paletě barvy](../windows/colors-window-image-editor-for-icons.md)vyberte levé tlačítko myši a vyberte barvu popředí nebo pravé tlačítko myši a vyberte barvu pozadí.

   - V [selektoru možností](../windows/toolbar-image-editor-for-icons.md)vyberte tvar představující štětec, který chcete použít.

1. Umístěte ukazatel na počáteční bod řádku.

1. Přetáhněte na koncový bod čáry.

### <a name="to-draw-a-closed-figure"></a>Vykreslení zavřeného obrázku

1. Použijte panel nástrojů **Editor obrázků** nebo přejít na **Obrázek** nabídky > **nástroje** a vyberte nástroj pro **Kreslení s uzavřenými titulky** .

   Nástroje pro **Kreslení s uzavřenými** obrázky vytvářejí hodnoty, které jsou uvedeny na příslušných tlačítkách.

1. V případě potřeby vyberte barvy a tloušťku čáry.

1. Přesuňte ukazatel na jeden roh obdélníkové oblasti, ve které chcete obrázek nakreslit.

1. Přetáhněte ukazatel na úhlopříčně opačný roh.

## <a name="custom-brushes"></a>Vlastní štětce

Vlastní štětec je obdélníková část obrázku, kterou jste vybrali, a použijte jako jeden z připravených štětců **editoru obrázků**. Všechny operace, které můžete provádět u výběru, můžete provádět také na vlastním štětce.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Vytvoření vlastního štětce z části obrázku

1. Vyberte část obrázku, kterou chcete použít pro štětec.

1. Podržte stisknutou klávesu **SHIFT** , vyberte výběr ve výběru a přetáhněte ho na obrázek nebo přejděte na **Obrázek** nabídky > **použít výběr jako štětec**.

   Váš výběr se zobrazí jako vlastní štětec, který distribuuje barvy ve výběru napříč obrázkem. Kopie výběru zůstanou podél cesty přetažení. Pomaleji jste přetáhli, tím více kopií provedete.

   > [!NOTE]
   > Výběr možnosti **použít jako štětec** bez předchozího výběru části obrázku bude používat celý obraz jako štětec. Výsledek použití vlastního štětce závisí také na tom, jestli jste vybrali [neprůhledné nebo průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Pixely ve vlastním štětci, které odpovídají aktuální barvě pozadí, jsou normálně transparentní: nebudou malovat na stávající obrázek. Toto chování můžete změnit tak, aby v pixelech barva pozadí bylo možné malovat přes existující obrázek.

Pomocí vlastního štětce jako razítko nebo vzorníku můžete vytvořit různé speciální efekty.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Kreslení vlastních tvarů štětce v barvě pozadí

1. Vyberte neprůhledné nebo průhledné pozadí.

1. Nastavte barvu pozadí na barvu, ve které chcete kreslit.

1. Umístěte vlastní štětec na místo, kam chcete kreslit.

1. Vyberte pravé tlačítko myši. V barvě pozadí jsou vykresleny všechny neprůhledné oblasti vlastního štětce.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Jak dvojnásobit nebo odpoloviční velikost vlastní velikosti štětce

Stisknutím klávesy **znaménka plus** ( **+** ) Zdvojnásobte velikost štětce nebo stiskněte klávesu **mínus znaménko** ( **-** ), abyste ji mohli rozpoloviční.

### <a name="to-cancel-the-custom-brush"></a>Postup zrušení vlastního štětce

Stiskněte klávesu **ESC** nebo zvolte jiný nástroj pro kreslení.

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)<br/>
[Postupy: vytvoření ikony nebo jiného obrázku](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Postupy: Úprava obrázku](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Postupy: práce s barvou](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
