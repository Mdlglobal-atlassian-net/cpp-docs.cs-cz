---
title: Editor obrázků pro ikony (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.texttool
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- editors, images
- resource editors [C++], graphics
- Image editor [C++]
- resource editors [C++], Image editor
- Image menu
- Grid Settings dialog box [C++]
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
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
ms.openlocfilehash: c411c4b95fcd3866c897f04b70da7cbb2b48ba28
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504310"
---
# <a name="image-editor-for-icons-c"></a>Editor obrázků pro ikony (C++)

Když vyberete soubor obrázku (třeba ICO, BMP, PNG) v **Průzkumníka řešení**, obrázek se otevře v **Editor obrázků** stejným způsobem, které se otevřou soubory kódu **Editor kódu** . Když **Editor obrázků** je aktivní karta, najdete v článku panely nástrojů s celou řadu nástrojů pro vytváření a úpravu obrázků. Spolu s rastrových obrázků, ikon a kurzorů můžete upravit obrázky ve formátu GIF nebo JPEG pomocí příkazů v **Image** nabídky a nástroje na **Editor obrázků** nástrojů.

Grafické prostředky jsou obrázky, které definujete pro vaši aplikaci. Můžete nakreslit OdRuky nebo kreslení tvarů pomocí. Můžete vybrat částí obrázku pro úpravy, převrácení nebo změnou velikosti, nebo můžete vytvořit vlastního štětce z vybrané části obrázku a kreslit štětcem této. Můžete definovat vlastnosti bitové kopie, uložit obrázky v různých formátech a převést imagí z jednoho formátu do druhého.

> [!NOTE]
> Použití **Editor obrázků**, můžete zobrazit obrázky 32-bit, ale nemůžete je upravovat.

Můžete také použít **Editor obrázků** a [binární Editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

Kromě vytvoření nové grafické prostředky, můžete [import existujících imagí](../windows/how-to-copy-resources.md#import-and-export-resources) pro úpravy a poté je přidejte do projektu. Můžete také otevřít a upravit bitové kopie, které nejsou součástí projektu pro [samostatný obrázek úpravy](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md).

Informace o tom, **Editor obrázků**, naleznete v tématu Jak [vytvoření ikony nebo jiný obrázek](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), [upravit obrázek](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), [pomocí nástroje kreslení](../windows/using-a-drawing-tool-image-editor-for-icons.md), [Pracovat s barvou](../windows/working-with-color-image-editor-for-icons.md), a [klávesové zkratky](../windows/accelerator-keys-image-editor-for-icons.md).

> [!NOTE]
> Stáhněte si zdarma **knihovna obrázků Visual Studio** obsahující mnoho animací, bitmap a ikon, které můžete použít ve svých aplikacích. Další informace o stažení knihovny naleznete v tématu [knihovna obrázků Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

## <a name="image-menu"></a>Nabídka obrázku

**Image** nabídky, která se zobrazí pouze tehdy, když **Editor obrázků** je aktivní, obsahuje příkazy pro úpravy obrázků, Správa palet barev a nastavení **Editor obrázků** okna Možnosti. Příkazy pro použití imagí zařízení jsou také k dispozici při práci s ikonami a kurzory.

|Příkaz|Popis|
|---|---|
|**Invertovat barvy**|Invertuje barev.|
|**Flip Horizontal**|Převrátí obrázek nebo výběr vodorovně.|
|**Převrátit svisle**|Převrátí obrázek nebo výběr svisle.|
|**Otočit o 90 stupňů**|Otočí obrázek nebo výběr o 90 stupňů.|
|**Zobrazit okno barev**|Otevře **barvy** okno, ve kterém můžete zvolit barev použitých pro vaši image.|
|**Použít výběr jako štětce**|Umožňuje vytvořit vlastní štětec z část obrázku.<br/><br/>Váš výběr se změní vlastní štětec, který distribuuje barev ve výběru mezi bitovou kopii. Zkopíruje výběr jsou ponechána na cestě přetahování. Tím pomaleji se při přetahování, jsou provedeny další kopie.|
|**Kopírování a výběr osnovy**|Vytvoří kopii aktuálního výběru a zvýrazní ji.<br/><br/>Pokud barvu pozadí je obsažen v aktuálním výběru, bude vyloučena v případě, že máte transparentní vybrané.
|**Upravit barvy**|Otevře **výběr vlastní barvy**, které umožňuje přizpůsobit barvy, můžete použít pro vaši image.|
|**Načíst paletu**|Otevře **načíst barvy palety** dialogové okno, které umožňuje načíst barvy palety dříve uložený soubor .pal.|
|**Uložit paletu**|Uloží do souboru .pal barvy palety.|
|**Nakreslit neprůhledné**|Pokud je vybráno, změní aktuální výběr neprůhledné.<br/><br/>Není-li zaškrtnuto, změní aktuální výběr na průhledný.|
|**Editor panelu nástrojů**|Otevře [nový prostředek panelu nástrojů – dialogové okno](../windows/new-toolbar-resource-dialog-box.md).|
|**Nastavení mřížky**|Otevře **nastavení mřížky** dialogovému oknu, ve kterém můžete zadat mřížky pro vaši image.|
|**Nový typ obrázku**|Otevře [nový \<zařízení > obrázku dialogové okno](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md).<br/><br/>Jedna ikona prostředků může obsahovat několik imagí různých velikostí a windows můžete použít velikost příslušnou položku v závislosti na tom, jak se bude zobrazený. Nový typ zařízení nemění velikost ikony, ale místo toho vytvoří novou image v rámci ikonu. Platí jenom pro ikony a kurzory.|
|**Aktuální typ obrázku ikony nebo kurzoru**|Otevře se podnabídka, který obsahuje seznam prvních devět dostupných imagí kurzoru nebo ikonu. Poslední příkaz v podnabídce **Další**, se otevře [otevřít \<zařízení > obrázku dialogové](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Smazat bitovou kopii**|Odstraní image vybrané zařízení.|
|**Nástroje**|Spustí podnabídku obsahující všechny nástroje, které jsou k dispozici **Editor obrázků** nástrojů.|

**Nastavení mřížky** dialogové okno umožňuje zadat nastavení mřížky pro vaši image a zobrazí čáry mřížky upravený obrázek. Řádky jsou užitečné pro úpravy image, ale nejsou uloženy v rámci samotné.

|Vlastnost|Popis|
|---|---|
|**Mřížka pixelů**|Pokud je zaškrtnuto, zobrazí mřížky kolem každý pixel v **Editor obrázků**.<br/><br/>Mřížky se zobrazí pouze na 4 x a vyšších rozlišení.|
|**Mřížka dlaždic**|Pokud je vybráno, zobrazí mřížky kolem bloky pixelů **Editor obrázků**, zadané mezery mezi hodnotami mřížky.|
|**Šířka**|Určuje šířku každého bloku dlaždice.<br/><br/>Tato vlastnost je užitečná při kreslení rastrové obrázky, který obsahuje více bitových kopií, které jsou uspořádány v pravidelných intervalech.|
|**Výška**|Určuje výšku každého bloku dlaždice.<br/><br/>Tato vlastnost je užitečná při kreslení rastrové obrázky, který obsahuje více bitových kopií, které jsou uspořádány v pravidelných intervalech.|

## <a name="toolbar"></a>Panel nástrojů

**Editor obrázků** nástrojů obsahuje nástroje pro kreslení, vykreslování, zadávání textu, mazání a manipulace s zobrazení. Obsahuje také výběr možnosti, pomocí kterého můžete vybrat možnosti používání jednotlivých nástrojích. Například můžete z různých šířky štětce, zvětšení faktorů a styly řádku.

Všechny nástroje, které jsou k dispozici na **Editor obrázků** nástrojů jsou také k dispozici v nabídce **Image** > **nástroje**. Použít **Editor obrázků** nástrojů a **možnost** vyberte nástroj pro výběr nebo možnost, že chcete.

![Panel nástrojů editoru obrázků](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")<br/>
**Editor obrázků** nástrojů

> [!TIP]
> Popisy tlačítek se zobrazí při přejeďte kurzorem přes tlačítko panelu nástrojů. Tyto tipy mohou pomoci identifikovat funkce každé tlačítko.

Protože mnoho kreslicí nástroje jsou k dispozici [klávesnice](../windows/accelerator-keys-image-editor-for-icons.md), někdy je užitečné, chcete-li skrýt **Editor obrázků** nástrojů.

- Chcete-li zobrazit nebo skrýt **Editor obrázků** nástrojů, přejděte do nabídky **zobrazení** > **panely nástrojů** a zvolte **Editor obrázků**.

> [!NOTE]
> Prvky z tohoto panelu nástrojů zobrazí nedostupný, pokud soubor obrázku z aktuálního projektu nebo řešení není otevřené v **Editor obrázků**.

### <a name="option-selector"></a>přepínač možnosti

S **možnost** selektor můžete určit šířku čáry, štětcem od ruky a další. Ikona na **možnost** selektor tlačítko se změní v závislosti na tom nástroje, které jste vybrali.

![Kreslení&#45;selektor tvar na panelu nástrojů editoru obrázků](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")<br/>
**Možnost** selektor na **Editor obrázků** nástrojů

### <a name="text-tool"></a>Nástroj text

Použití **textový nástroj** dialogové okno Přidat text do prostředku kurzoru, rastrový obrázek nebo ikonu.

Chcete-li získat přístup k tomuto dialogovému oknu, otevřete **Editor obrázků** a přejděte do nabídky **Image** > **nástroje**a pak **textový nástroj** příkaz.

> [!TIP]
> Klepnutí pravým tlačítkem myši na **textový nástroj** dialogové okno pro přístup k výchozí místní nabídka, která obsahuje seznam standardních příkazů Windows.

Otevřít **písmo nástroje Text** dialogové okno Změnit písmo, styl nebo velikost písma kurzoru. Změny se použijí pro text zobrazený v **Text** oblasti.

Chcete-li získat přístup k tomuto dialogovému oknu, vyberte **písmo** tlačítko **textový nástroj** dialogové okno. Dostupné vlastnosti jsou:

|Vlastnost|Popis|
|---|---|
|**Písma**|Zobrazí seznam dostupných písem.|
|**Styl písma**|Zobrazí seznam dostupných stylů pro zadaný font.|
|**Velikost**|Umožňuje zobrazit seznam velikostí bod k dispozici pro zadaný font.|
|**Ukázka**|Zobrazuje ukázku toho, jak se text zobrazí s nastavením zadaný font.|
|**skript**|Zobrazí seznam dostupný jazyk skriptů pro zadaný font.<br/><br/>Když vyberete jiný jazyk skriptu, znaková sada, bude k dispozici pro vytvoření vícejazyčné dokumenty jazyka.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>Změna písma textu obrázku

Tady je příklad toho, jak přidat text do ikony v aplikaci Windows a manipulaci s písmo textu.

1. Vytvoření aplikace C++ Windows Forms. Podrobnosti najdete v tématu [jak: Vytvoření aplikace Windows Forms](/previous-versions/visualstudio/visual-studio-2008/s69bf10x(v%3dvs.90)). *App.ico* ve výchozím nastavení se přidá do projektu soubor.

1. V **Průzkumníka řešení**, poklikejte na soubor *app.ico*. **Editor obrázků** se otevře.

1. Přejděte do nabídky **Image** > **nástroje** a vyberte **textový nástroj**.

1. V **textový nástroj** dialogovém okně *C++* v oblasti prázdný text. Tento text se zobrazí v okně možností změny velikosti se nachází v levém horním rohu *app.ico* v **Editor obrázků**.

1. V **Editor obrázků**, přetáhněte pole umožňující změnu velikosti na střed *app.ico* pro lepší čitelnost textu.

1. V **textový nástroj** dialogové okno, vyberte **písmo** tlačítko.

1. V **písmo nástroje Text** dialogové okno:

   - Vyberte **časy New Roman** ze seznamu dostupných písem, které jsou uvedeny v **písmo** pole se seznamem.

   - Vyberte **tučné** ze seznamu styly dostupné písmo, které jsou uvedené v **styl písma** pole se seznamem.

   - Vyberte **10** ze seznamu dostupných bodů velikosti uvedené v **velikost** pole se seznamem.

   - Zvolte **OK**. **Písmo nástroje Text** dialogové okno se zavře a použije se nové nastavení písma v textu.

1. Zvolte **Zavřít** na **textový nástroj** dialogové okno. Pole umožňující změnu velikosti celého textu zmizí z **Editor obrázků**.

Oblasti text se zobrazí text, který se zobrazí jako součást zdroje. Tato oblast je původně prázdná.

> [!NOTE]
> Pokud **průhledné pozadí** je nastavena pouze text, se umístí do bitové kopie. Pokud **neprůhledné pozadí** je nastaven, ohraničující obdélník, vyplněn barvou pozadí se umístí za text.

## <a name="window-panes"></a>Podokna

**Editor obrázků** okno naleznete dvě zobrazení obrázku s rozdělovačem dvě podokna pro rozdělení. Můžete přetáhnout příčku ze strany na stranu, a změnit tak relativní velikosti podoken. Aktivní podokno zobrazuje hranici výběru.

Jedno zobrazení je skutečná velikost a druhý je rozšířeno o výchozí faktor zvětšení 6. Zobrazení v těchto dvou podoken se automaticky aktualizují, všechny změny provedené v jedno podokno se okamžitě zobrazí v jiném. Velikost podoken usnadňují práci na zvětšeným zobrazením bitové kopie, ve kterém můžete rozlišení jednotlivých pixelech a, ve stejnou dobu, můžete sledovat účinek práce na zobrazení skutečné velikosti obrázku.

V levém podokně používá tolik místa je potřeba (až do výše polovinu **Image** okno) zobrazit výchozí zobrazení 1:1 zvětšení obrázku. V pravém podokně se zobrazí výchozí obrázek 6:1 zvětšení přiblížení či oddálení. Můžete změnit zvětšení v každé pomocí podokna **Magnify** nástroj **Editor obrázků** nástrojů nebo pomocí klávesové zkratky.

Můžete zvětšit menší podokně **Editor obrázků** okno a použijte dvě podokna pro zobrazení různých oblastech velký obrázek. Vyberte v podokně zvolte jej.

Můžete změnit tak relativní velikosti podoken umístěním ukazatele na panelu rozdělení a přesunutí příčku směrem doprava nebo doleva. Pokud budete chtít pracovat na pouze jedno podokno, můžete příčku přesunout až po obou stranách.

Pokud **Editor obrázků** podokno se zvětšeným faktorem 4 nebo vyšší, můžete zobrazit mřížku obrazových bodů, který vymezuje jednotlivých pixelech na obrázku.

### <a name="to-change-the-magnification-factor"></a>Chcete-li změnit faktor zvětšení

Ve výchozím nastavení **Editor obrázků** zobrazí v levém podokně na skutečné velikosti a zobrazení v pravém podokně ve skutečné velikosti 6krát. Faktoru zvětšení (prohlédnout ve stavovém řádku v dolní části pracovní prostor) je poměr mezi skutečná velikost bitové kopie a velikost. Výchozí faktor je 6 a rozsah je od 1 do 10.

1. Vyberte **Editor obrázků** podokně jehož faktor zvětšení, které chcete změnit.

1. Na **Editor obrázků** nástrojů, vyberte šipku vpravo od **Magnify** nástroje a vyberte faktor zvětšení z podnabídky: **1 X**, **2 X**, **6 X**, nebo **8 X**.

   > [!NOTE]
   > Vybrat faktor zvětšení kromě oprávnění uvedených v seznamu **Magnify** nástroj, použijte klávesy akcelerátoru.

### <a name="to-display-or-hide-the-pixel-grid"></a>K zobrazení nebo skrytí mřížky pixelů

Pro všechny **Editor obrázků** podoken s faktor zvětšení 4 nebo vyšší, můžete zobrazit mřížku oddělující jednotlivé pixelů na obrázku.

1. Přejděte do nabídky **Image** > **nastavení mřížky**.

1. Vyberte **mřížku obrazových bodů** zaškrtávací políčko pro zobrazení mřížky, nebo zrušte zaškrtnutí políčka Skrýt mřížku.

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také:

[Editory prostředků](../windows/resource-editors.md)<br/>
[Ikony](/windows/desktop/menurc/icons)