---
title: Panel nástrojů (C++ Editor obrázků pro ikony)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.texttool
helpviewer_keywords:
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
- toolbars [C++], showing
- toolbars [C++], hiding
- text, adding to an image
- Text Tool dialog box [C++]
- Text Tool Font dialog box [C++]
- fonts, changing on an image
- text, on images
ms.assetid: a0af4209-6273-4106-a7c1-0edecc9b5755
ms.openlocfilehash: dfbd721afd997f3151b1c20a7e0e1fb60e0c83e4
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560319"
---
# <a name="toolbar-c-image-editor-for-icons"></a>Panel nástrojů (C++ Editor obrázků pro ikony)

**Editor obrázků** nástrojů obsahuje nástroje pro kreslení, vykreslování, zadávání textu, mazání a manipulace s zobrazení. Obsahuje také výběr možnosti, pomocí kterého můžete vybrat možnosti používání jednotlivých nástrojích. Například můžete z různých šířky štětce, zvětšení faktorů a styly řádku.

> [!NOTE]
> Všechny nástroje, které jsou k dispozici na **Editor obrázků** nástrojů jsou také k dispozici **Image** nabídky (v části **nástroje** příkaz).

![Panel nástrojů editoru obrázků](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar") panelu nástrojů editoru obrázků

Použít **Editor obrázků** nástrojů a **možnost** vyberte nástroj pro výběr nebo možnost, že chcete.

> [!TIP]
> Popisy tlačítek se zobrazí při přejeďte kurzorem přes tlačítko panelu nástrojů. Tyto tipy mohou pomoci identifikovat funkce každé tlačítko.

S **možnost** selektor můžete určit šířku čáry, štětcem od ruky a další. Ikona na **možnost** selektor tlačítko se změní v závislosti na tom nástroje, které jste vybrali.

![Kreslení&#45;selektor tvar na panelu nástrojů editoru obrázků](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector") výběr možnosti na panelu nástrojů editoru obrázků

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="use-the-text-tool-dialog-box"></a>Použijte dialogové okno textový nástroj

Použití **textový nástroj** dialogové okno Přidat text do prostředku kurzoru, rastrový obrázek nebo ikonu.

Chcete-li získat přístup k tomuto dialogovému oknu, otevřete [Editor obrázků](../windows/window-panes-image-editor-for-icons.md). Vyberte **nástroje** z **Image** nabídky a pak vyberte **textový nástroj** příkazu.

### <a name="font-button"></a>Tlačítko písma

Otevře **písmo nástroje Text** dialogové okno, ve kterém můžete změnit písmo, styl nebo velikost písma kurzoru. Změny se použijí pro text zobrazený v **Text** oblasti.

Chcete-li získat přístup k tomuto dialogovému oknu, vyberte **písmo** tlačítko **textový nástroj** dialogové okno. Dostupné vlastnosti jsou:

|Vlastnost|Popis|
|---|---|
|**Písma**|Zobrazí seznam dostupných písem.|
|**Styl písma**|Zobrazí seznam dostupných stylů pro zadaný font.|
|**Velikost**|Umožňuje zobrazit seznam velikostí bod k dispozici pro zadaný font.|
|**Ukázka**|Zobrazuje ukázku toho, jak se text zobrazí s nastavením zadaný font.|
|**skript**|Zobrazí seznam dostupný jazyk skriptů pro zadaný font. Když vyberete jiný jazyk skriptu, znaková sada, bude k dispozici pro vytvoření vícejazyčné dokumenty jazyka.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>Změna písma textu obrázku

Následující postup je příklad toho, jak přidat text do ikony v aplikaci Windows a manipulaci s písmo textu.

1. Vytvoření aplikace C++ Windows Forms. Podrobnosti najdete v tématu [vytvoření projektu aplikace Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5). *App.ico* ve výchozím nastavení se přidá do projektu soubor.

1. V **Průzkumníka řešení**, poklikejte na soubor *app.ico*. [Editor obrázků](../windows/image-editor-for-icons.md) se otevře.

1. Z **Image** nabídce vyberte možnost **nástroje** a pak vyberte **textový nástroj**. **Textový nástroj** se zobrazí dialogové okno.

1. V **textový nástroj** dialogovém okně *C++* v oblasti prázdný text. Tento text se zobrazí v okně možností změny velikosti se nachází v levém horním rohu *app.ico*v **Editor obrázků**.

1. V **Editor obrázků**, přetáhněte pole umožňující změnu velikosti na střed app.ico, aby se zlepšila čitelnost textu.

1. V **textový nástroj** dialogové okno, vyberte **písmo** tlačítko. **Písmo nástroje Text** se zobrazí dialogové okno.

1. V **písmo nástroje Text** dialogu **časy New Roman** ze seznamu dostupných písem, které jsou uvedeny v **písmo** pole se seznamem.

1. Vyberte **tučné** ze seznamu styly dostupné písmo, které jsou uvedené v **styl písma** pole se seznamem.

1. Vyberte **10** ze seznamu dostupných bodů velikosti uvedené v **velikost** pole se seznamem.

1. Vyberte tlačítko **OK**. **Písmo nástroje Text** dialogové okno se zavře a použije se nové nastavení písma v textu.

1. Vyberte **Zavřít** tlačítko **textový nástroj** dialogové okno. Pole umožňující změnu velikosti celého textu zmizí z **Editor obrázků**.

### <a name="text-area"></a>Textové pole

Zobrazí text, který se zobrazí jako součást zdroje. Tato oblast je původně prázdná.

> [!NOTE]
> Pokud **průhledné pozadí** je nastavena pouze text, se umístí do bitové kopie. Pokud **neprůhledné pozadí** nastavena ohraničující obdélník, naplní se [barva pozadí](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md), se umístí za text. Další informace najdete v tématu [výběr neprůhledných a průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Klepnutí pravým tlačítkem myši na **textový nástroj** dialogové okno pro přístup k výchozí místní nabídka, která obsahuje seznam standardních příkazů Windows.

## <a name="to-display-or-hide-the-image-editor-toolbar"></a>K zobrazení nebo skrytí panelu nástrojů editoru obrázků

Protože mnoho kreslicí nástroje jsou k dispozici [klávesnice](../windows/accelerator-keys-image-editor-for-icons.md), někdy je užitečné, chcete-li skrýt **Editor obrázků** nástrojů.

Na **zobrazení** nabídce vyberte možnost **panely nástrojů** klikněte na tlačítko **Editor obrázků**.

   > [!NOTE]
   > Prvky z tohoto panelu nástrojů zobrazí nedostupný, pokud soubor obrázku z aktuálního projektu nebo řešení není otevřené v **Editor obrázků**. Zobrazit [vytvoření ikony nebo jiný obrázek](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), informace o přidávání souborů obrázků do vašich projektů.

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také

[Okno barvy](../windows/colors-window-image-editor-for-icons.md)<br/>
[Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>