---
title: Editor obrázků pro ikony
ms.date: 10/17/2018
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
ms.openlocfilehash: 48b363b7b9021042fe6242be70c74f0daeade0c2
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320702"
---
# <a name="image-editor-for-icons"></a>Editor obrázků pro ikony

Když kliknete na soubor obrázku (třeba ICO, BMP, PNG) v Průzkumníku řešení, obraz se otevře v editoru obrázků stejně jako kód soubory otevřené v editoru kódu. Když je aktivní karta editoru obrázků, se zobrazí panely nástrojů s celou řadu nástrojů pro vytváření a úpravu obrázků. Spolu s rastrových obrázků, ikon a kurzorů můžete upravit obrázky ve formátu GIF nebo JPEG pomocí příkazů v **Image** nabídky a nástroje na **Editor obrázků** nástrojů.

Grafické prostředky jsou obrázky, které definujete pro vaši aplikaci. Můžete nakreslit OdRuky nebo kreslení tvarů pomocí. Můžete vybrat částí obrázku pro úpravy, převrácení nebo změnou velikosti, nebo můžete vytvořit vlastního štětce z vybrané části obrázku a kreslit štětcem této. Můžete definovat vlastnosti bitové kopie, uložit obrázky v různých formátech a převést imagí z jednoho formátu do druhého.

Kromě vytvoření nové grafické prostředky, můžete [import existujících imagí](../windows/how-to-import-and-export-resources.md) pro úpravy a poté je přidejte do projektu. Můžete také otevřít a upravit bitové kopie, které nejsou součástí projektu pro [samostatný obrázek úpravy](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md).

> [!NOTE]
> Použití **Editor obrázků**, můžete zobrazit obrázky 32-bit, ale nemůžete je upravovat.

Editou obrázků vám umožňuje:

- [Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)

- [Práce s ikonami a kurzory: Prostředky obrázků pro zobrazovací zařízení](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

- [Používat klíče akcelerátoru pro příkazy v editoru obrázků](../windows/accelerator-keys-image-editor-for-icons.md)

**Editor obrázků** okno naleznete dvě zobrazení obrázku s rozdělovačem dvě podokna pro rozdělení. Můžete přetáhnout příčku ze strany na stranu, a změnit tak relativní velikosti podoken. Aktivní podokno zobrazuje hranici výběru.

**Editor obrázků** okna můžete upravit podle vašich potřeb a preferencí. Je možné [změnit faktor zvětšení](../windows/changing-the-magnification-factor-image-editor-for-icons.md) a [zobrazit nebo skrýt mřížku obrazových bodů](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md).

> [!NOTE]
> Použití **Editor obrázků**, můžete zobrazit obrázky 32-bit, ale nemůžete je upravovat.

## <a name="image-menu"></a>Nabídka obrázku

**Image** nabídky, která se zobrazí pouze tehdy, když **Image** editor není aktivní, obsahuje příkazy pro úpravy obrázků, Správa palet barev a nastavení **Editor obrázků** okna Možnosti. Příkazy pro použití imagí zařízení jsou také k dispozici při práci s ikonami a kurzory.

|Příkaz|Popis|
|---|---|
|**Invertovat barvy**|Invertuje barev. Další informace najdete v tématu [převrácení barev ve výběru](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md).|
|**Flip Horizontal**|Převrátí obrázek nebo výběr vodorovně. Další informace najdete v tématu [překlopení obrázku](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Převrátit svisle**|Převrátí obrázek nebo výběr svisle. Další informace najdete v tématu [překlopení obrázku](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Otočit o 90 stupňů**|Otočí obrázek nebo výběr o 90 stupňů. Další informace najdete v tématu [překlopení obrázku](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Zobrazit okno barev**|Otevře [okno barvy](../windows/colors-window-image-editor-for-icons.md), ve kterém můžete zvolit barev použitých pro vaši image. Další informace najdete v tématu [práce s barvou](../windows/working-with-color-image-editor-for-icons.md).|
|**Použít výběr jako štětce**|Umožňuje vytvořit vlastní štětec z část obrázku. Váš výběr se změní vlastní štětec, který distribuuje barev ve výběru mezi bitovou kopii. Zkopíruje výběr jsou ponechána na cestě přetahování. Tím pomaleji se při přetahování, jsou provedeny další kopie. Další informace najdete v tématu [vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).|
|**Kopírování a výběr osnovy**|Vytvoří kopii aktuálního výběru a zvýrazní ji. Pokud je barva pozadí obsažen v aktuálním výběru, bude vyloučena Pokud jste [transparentní](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) vybrané.
|**Upravit barvy**|Otevře [výběr vlastní barvy](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md), které umožňuje přizpůsobit barvy, můžete použít pro vaši image. Další informace najdete v tématu [přizpůsobení nebo změna barev](../windows/customizing-or-changing-colors-image-editor-for-icons.md).|
|**Načíst paletu**|Otevře [dialogové okno Načíst barvy palety](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), což vám umožní načíst barvy palety dříve uložený soubor .pal.|
|**Uložit paletu**|Uloží do souboru .pal barvy palety.|
|**Nakreslit neprůhledné**|Pokud je vybráno, změní aktuální výběr neprůhledné. Není-li zaškrtnuto, změní aktuální výběr na průhledný. Další informace najdete v tématu [výběr neprůhledné nebo průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|**Editor panelu nástrojů**|Otevře [nový prostředek panelu nástrojů – dialogové okno](../windows/new-toolbar-resource-dialog-box.md).|
|**Nastavení mřížky**|Otevře **nastavení mřížky** dialogovému oknu, ve kterém můžete zadat mřížky pro vaši image.|
|**Nový typ obrázku**|Otevře [nový \<zařízení > obrázku dialogové okno](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md). Jedna ikona prostředků může obsahovat několik imagí různých velikostí a windows můžete použít velikost příslušnou položku v závislosti na tom, jak se bude zobrazený. Nový typ zařízení nemění velikost ikony, ale místo toho vytvoří novou image v rámci ikonu. Platí jenom pro ikony a kurzory.|
|**Aktuální typ obrázku ikony nebo kurzoru**|Otevře se podnabídka, který obsahuje seznam prvních dostupné kurzoru nebo ikonu imagí (prvních devět). Poslední příkaz v podnabídce **více...** , otevře [otevřít \<zařízení > obrázku dialogové](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Smazat bitovou kopii**|Odstraní image vybrané zařízení.|
|**Nástroje**|Spustí podnabídku obsahující všechny nástroje, které jsou k dispozici [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md).|

**Nastavení mřížky** dialogové okno umožňuje zadat nastavení mřížky pro vaši image a zobrazí čáry mřížky upravený obrázek. Řádky jsou užitečné pro úpravy image, ale nejsou uloženy v rámci samotné.

|Vlastnost|Popis|
|---|---|
|**Mřížka pixelů**|Pokud je zaškrtnuto, zobrazí v editoru obrázků do mřížky kolem každý pixel. Mřížky se zobrazí pouze na 4 x a vyšších rozlišení.|
|**Mřížka dlaždic**|Při výběru zobrazí v editoru obrázků, určený hodnotami mezery mřížky mřížky kolem bloky v pixelech.|
|**Šířka**|Určuje šířku každého bloku dlaždice. Tato vlastnost je užitečná při kreslení rastrové obrázky, který obsahuje více bitových kopií, které jsou uspořádány v pravidelných intervalech.|
|**Výška**|Určuje výšku každého bloku dlaždice. Tato vlastnost je užitečná při kreslení rastrové obrázky, který obsahuje více bitových kopií, které jsou uspořádány v pravidelných intervalech.|

## <a name="toolbar"></a>Panel nástrojů

**Editor obrázků** nástrojů obsahuje nástroje pro kreslení, vykreslování, zadávání textu, mazání a manipulace s zobrazení. Obsahuje také výběr možnosti, pomocí kterého můžete vybrat možnosti používání jednotlivých nástrojích. Například můžete z různých šířky štětce, zvětšení faktorů a styly řádku.

> [!NOTE]
> Všechny nástroje, které jsou k dispozici na **Editor obrázků** nástrojů jsou také k dispozici **Image** nabídky (v části **nástroje** příkaz).

![Panel nástrojů editoru obrázků](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar") panelu nástrojů editoru obrázků

Použít **Editor obrázků** nástrojů a **možnost** vyberte nástroj pro výběr nebo možnost, že chcete.

> [!TIP]
> Popisy tlačítek se zobrazí při přejeďte kurzorem přes tlačítko panelu nástrojů. Tyto tipy mohou pomoci identifikovat funkce každé tlačítko.

S **možnost** selektor můžete určit šířku čáry, štětcem od ruky a další. Ikona na **možnost** selektor tlačítko se změní v závislosti na tom nástroje, které jste vybrali.

![Kreslení&#45;selektor tvar na panelu nástrojů editoru obrázků](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector") výběr možnosti na panelu nástrojů editoru obrázků

### <a name="use-the-text-tool-dialog-box"></a>Použijte dialogové okno textový nástroj

Použití **textový nástroj** dialogové okno Přidat text do prostředku kurzoru, rastrový obrázek nebo ikonu.

Chcete-li získat přístup k tomuto dialogovému oknu, otevřete [Editor obrázků](../windows/window-panes-image-editor-for-icons.md). Vyberte **nástroje** z **Image** nabídky a pak vyberte **textový nástroj** příkazu.

#### <a name="font-button"></a>Tlačítko písma

Otevře **písmo nástroje Text** dialogové okno, ve kterém můžete změnit písmo, styl nebo velikost písma kurzoru. Změny se použijí pro text zobrazený v **Text** oblasti.

Chcete-li získat přístup k tomuto dialogovému oknu, vyberte **písmo** tlačítko **textový nástroj** dialogové okno. Dostupné vlastnosti jsou:

|Vlastnost|Popis|
|---|---|
|**Písma**|Zobrazí seznam dostupných písem.|
|**Styl písma**|Zobrazí seznam dostupných stylů pro zadaný font.|
|**Velikost**|Umožňuje zobrazit seznam velikostí bod k dispozici pro zadaný font.|
|**Ukázka**|Zobrazuje ukázku toho, jak se text zobrazí s nastavením zadaný font.|
|**skript**|Zobrazí seznam dostupný jazyk skriptů pro zadaný font. Když vyberete jiný jazyk skriptu, znaková sada, bude k dispozici pro vytvoření vícejazyčné dokumenty jazyka.|

Změna písma textu obrázku:

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

#### <a name="text-area"></a>Textové pole

Zobrazí text, který se zobrazí jako součást zdroje. Tato oblast je původně prázdná.

> [!NOTE]
> Pokud **průhledné pozadí** je nastavena pouze text, se umístí do bitové kopie. Pokud **neprůhledné pozadí** nastavena ohraničující obdélník, naplní se [barva pozadí](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md), se umístí za text. Další informace najdete v tématu [výběr neprůhledných a průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Klepnutí pravým tlačítkem myši na **textový nástroj** dialogové okno pro přístup k výchozí místní nabídka, která obsahuje seznam standardních příkazů Windows.

### <a name="to-display-or-hide-the-image-editor-toolbar"></a>K zobrazení nebo skrytí panelu nástrojů editoru obrázků

Protože mnoho kreslicí nástroje jsou k dispozici [klávesnice](../windows/accelerator-keys-image-editor-for-icons.md), někdy je užitečné, chcete-li skrýt **Editor obrázků** nástrojů.

Na **zobrazení** nabídce vyberte možnost **panely nástrojů** klikněte na tlačítko **Editor obrázků**.

   > [!NOTE]
   > Prvky z tohoto panelu nástrojů zobrazí nedostupný, pokud soubor obrázku z aktuálního projektu nebo řešení není otevřené v **Editor obrázků**. Zobrazit [vytvoření ikony nebo jiný obrázek](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), informace o přidávání souborů obrázků do vašich projektů.

## <a name="window-panes"></a>Podokna

**Editor obrázků** okno obvykle zobrazí obrázek do dvou podoken oddělené rozdělovač. Jedno zobrazení je skutečná velikost a druhý se zvětší (výchozí rozšíření faktor je 6). Zobrazení v těchto dvou podoken se automaticky aktualizují: změny, které provedete v jedno podokno se okamžitě zobrazí v jiném. Velikost podoken usnadňují práci na zvětšeným zobrazením bitové kopie, ve kterém můžete rozlišení jednotlivých pixelech a, ve stejnou dobu, můžete sledovat účinek práce na zobrazení skutečné velikosti obrázku.

V levém podokně používá tolik místa je potřeba (až polovinu **Image** okno) Chcete-li zobrazit zobrazení zvětšením 1:1 (výchozí) z image. Pravý panel zobrazuje přiblíženou bitové kopie (6:1 zvětšení ve výchozím nastavení). Můžete změnit zvětšení v každé pomocí podokna **Magnify** nástroj [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) nebo pomocí klávesové zkratky.

Můžete zvětšit menší podokně **Editor obrázků** okno a použijte dvě podokna pro zobrazení různých oblastech velký obrázek. Vyberte v podokně zvolte jej.

Můžete změnit tak relativní velikosti podoken umístěním ukazatele na panelu rozdělení a přesunutí příčku směrem doprava nebo doleva. Pokud budete chtít pracovat na pouze jedno podokno, můžete příčku přesunout až po obou stranách.

Pokud **Editor obrázků** podokno se zvětšeným faktorem 4 nebo vyšší, můžete zobrazit mřížku obrazových bodů, který vymezuje jednotlivých pixelech na obrázku.

### <a name="to-change-the-magnification-factor"></a>Chcete-li změnit faktor zvětšení

Ve výchozím nastavení **Image** editoru se zobrazí v levém podokně ve skutečné velikosti zobrazení a zobrazení v pravém podokně na 6 časů skutečnou velikost. Faktoru zvětšení (prohlédnout ve stavovém řádku v dolní části pracovní prostor) je poměr mezi skutečná velikost bitové kopie a velikost. Výchozí faktor je 6 a rozsah je od 1 do 10.

1. Vyberte **Editor obrázků** podokně jehož faktor zvětšení, které chcete změnit.

1. Na [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md), vyberte šipku vpravo od [nebo vypne nástroj zvětšení](../windows/toolbar-image-editor-for-icons.md) a vyberte faktor zvětšení z podnabídky: **1 X**, **2 X**, **6 X**, nebo **8 X**.

   > [!NOTE]
   > Vybrat faktor zvětšení kromě oprávnění uvedených v seznamu **Magnify** nástroj, použijte klávesy akcelerátoru.

### <a name="to-display-or-hide-the-pixel-grid"></a>K zobrazení nebo skrytí mřížky pixelů

Pro všechny **Editor obrázků** podoken s faktor zvětšení 4 nebo vyšší, můžete zobrazit mřížku oddělující jednotlivé pixelů na obrázku.

1. Na **Image** nabídce vyberte možnost **nastavení mřížky**.

1. Vyberte **mřížku obrazových bodů** zaškrtávací políčko pro zobrazení mřížky, nebo zrušte zaškrtnutí políčka Skrýt mřížku.

> [!TIP]
> Popisy tlačítek se zobrazí při přejeďte kurzorem přes tlačítko panelu nástrojů. Tyto tipy mohou pomoci identifikovat funkce každé tlačítko.

## <a name="visual-studio-image-library"></a>Knihovna obrázků Visual Studio

Zdarma si můžete stáhnout **knihovna obrázků Visual Studio** obsahující mnoho animací, bitmap a ikon, které můžete použít ve svých aplikacích. Další informace o stažení knihovny naleznete v tématu [The knihovna obrázků Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

## <a name="managed-resources"></a>Spravované prostředky

Můžete použít **Image** editoru a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také:

[Editory prostředků](../windows/resource-editors.md)<br/>
[Ikony](https://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)