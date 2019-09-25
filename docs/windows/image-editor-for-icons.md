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
ms.openlocfilehash: 0f8fe228b804538b6a0d0377f05d79c34e787587
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "69514217"
---
# <a name="image-editor-for-icons-c"></a>Editor obrázků pro ikony (C++)

Když v **Průzkumník řešení**vyberete soubor obrázku (například. ico,. bmp,. png), obrázek se otevře v **editoru obrázků** stejným způsobem jako soubory kódu otevřené v **editoru kódu**. Když je aktivní karta **editoru obrázků** , uvidíte panely nástrojů s mnoha nástroji pro vytváření a úpravu obrázků. Spolu s rastrovými obrázky, ikonami a kurzory můžete upravovat obrázky ve formátu GIF nebo JPEG pomocí příkazů v nabídce **Obrázek** a nástroje na panelu nástrojů **Editor obrázků** .

Grafické prostředky jsou bitové kopie, které definujete pro aplikaci. Můžete nakreslit FreeHand nebo kreslit pomocí tvarů. Můžete vybrat části obrázku pro úpravy, překlopení nebo změnu velikosti nebo můžete vytvořit vlastní štětce z vybrané části obrázku a kreslit pomocí tohoto štětce. Můžete definovat vlastnosti obrázku, ukládat obrázky v různých formátech a převádět obrázky z jednoho formátu na jiný.

> [!NOTE]
> Pomocí **editoru obrázků**můžete zobrazovat 32 bitové kopie, ale nemůžete je upravovat.

Můžete také použít **Editor obrázků** a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků sady Visual Studio nepodporují úpravu integrovaných prostředků.

Kromě vytváření nových grafických prostředků můžete [importovat existující image](../windows/how-to-copy-resources.md#import-and-export-resources) pro úpravy a pak je přidat do projektu. Můžete také otevřít a upravit obrázky, které nejsou součástí projektu pro úpravu samostatného [obrázku](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md).

Informace o **editoru obrázků**najdete v tématu Jak [vytvořit ikonu nebo jiný obrázek](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), [Upravit obrázek](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), [použít nástroj pro kreslení](../windows/using-a-drawing-tool-image-editor-for-icons.md), [pracovat s barvami](../windows/working-with-color-image-editor-for-icons.md)a [klávesovou zkratku](../windows/accelerator-keys-image-editor-for-icons.md).

> [!NOTE]
> Zdarma si stáhněte **knihovnu imagí sady Visual Studio** , která obsahuje mnoho animací, rastrových obrázků a ikon, které můžete použít ve svých aplikacích. Další informace o tom, jak stáhnout knihovnu, najdete v [knihovně imagí sady Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

## <a name="image-menu"></a>Nabídka obrázku

Nabídka **Obrázek** , která se zobrazí pouze v případě, že je **Editor obrázků** aktivní, obsahuje příkazy pro úpravu obrázků, správu palet barev a nastavení možností okna **editoru obrázků** . K dispozici jsou také příkazy pro používání imagí zařízení, když pracujete s ikonami a kurzory.

|Příkaz|Popis|
|---|---|
|**Invertovat barvy**|Invertuje barvy.|
|**Překlopit vodorovně**|Překlopí obrázek nebo výběr vodorovně.|
|**Převrátit svisle**|Překlopí obrázek nebo výběr svisle.|
|**Otočit o 90 stupňů**|Otočí obrázek nebo výběr o 90 stupňů.|
|**Zobrazit okno barev**|Otevře okno **barvy** , ve kterém můžete zvolit barvy, které chcete použít pro vaši image.|
|**Použít výběr jako štětec**|Umožňuje vytvořit vlastní štětce z části obrázku.<br/><br/>Váš výběr se zobrazí jako vlastní štětec, který distribuuje barvy ve výběru napříč obrázkem. Kopie výběru zůstanou podél cesty přetažení. Pomaleji jste přetáhli, tím více kopií provedete.|
|**Kopírovat a obrysový výběr**|Vytvoří kopii aktuálního výběru a objednává ho.<br/><br/>Pokud je barva pozadí obsažena v aktuálním výběru, bude vyloučena, pokud jste vybrali možnost transparentní.
|**Upravit barvy**|Otevře **vlastní selektor barev**, který umožňuje přizpůsobit barvy používané pro vaši image.|
|**Načíst paletu**|Otevře dialogové okno **paleta načtení barev** , ve kterém můžete načíst barvy palety, které byly dříve uloženy do souboru. PAL.|
|**Uložit paletu**|Uloží barvy palety do souboru. PAL.|
|**Kreslit neprůhledné**|Když se tato možnost vybere, převede aktuální výběr na neprůhledný.<br/><br/>Pokud je zaškrtnuto, převede aktuální výběr na průhledný.|
|**Editor panelu nástrojů**|Otevře se [dialogové okno nový prostředek panelu nástrojů](../windows/new-toolbar-resource-dialog-box.md).|
|**Nastavení mřížky**|Otevře dialogové okno **Nastavení mřížky** , ve kterém můžete pro svůj obrázek zadat mřížku.|
|**Nový typ obrázku**|Otevře [dialogové okno \<nový typ obrázku > zařízení](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md).<br/><br/>Jeden prostředek ikony může obsahovat několik imagí různých velikostí a systém Windows může použít vhodnou velikost ikony v závislosti na tom, jak se bude zobrazovat. Nový typ zařízení nemění velikost ikony, ale místo toho vytvoří novou image v rámci této ikony. Platí pouze pro ikony a kurzory.|
|**Aktuální ikona a typ obrázku ukazatele**|Otevře podnabídku, která obsahuje prvních devět dostupných imagí kurzoru nebo ikon. Poslední příkaz v podnabídce, **Další**, otevře [dialogové okno otevřít \<>ou bitovou kopii zařízení](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Odstranit typ obrázku**|Odstraní vybranou image zařízení.|
|**Nástroje**|Spustí podnabídku, která obsahuje všechny nástroje, které jsou k dispozici na panelu nástrojů **Editor obrázků** .|

Dialogové okno **Nastavení mřížky** umožňuje zadat nastavení mřížky pro obrázek a zobrazit čáry mřížky v upravované imagi. Řádky jsou užitečné pro úpravu obrázku, ale neukládají se jako součást samotné image.

|Vlastnost|Popis|
|---|---|
|**Mřížka pixelů**|Pokud je zaškrtnuto, zobrazí mřížku kolem každého pixelu v **editoru obrázků**.<br/><br/>Mřížka se zobrazí jenom na rozlišení 4 × a vyšší.|
|**Mřížka dlaždic**|Když se tato možnost vybere, zobrazí mřížku kolem bloků pixelů v **editoru obrázků**, která je určená hodnotami pro mezery mezi tabulkami.|
|**Délk**|Určuje šířku každého bloku dlaždice.<br/><br/>Tato vlastnost je užitečná, když kreslíte bitmapy obsahující více obrázků, které jsou uspořádány v pravidelných intervalech.|
|**Výška**|Určuje výšku každého bloku dlaždice.<br/><br/>Tato vlastnost je užitečná, když kreslíte bitmapy obsahující více obrázků, které jsou uspořádány v pravidelných intervalech.|

## <a name="toolbar"></a>Panel nástrojů

Panel nástrojů **Editor obrázků** obsahuje nástroje pro kreslení, malování, zadávání textu, mazání a manipulaci s zobrazeními. Obsahuje také selektor možností, ve kterém můžete vybrat možnosti pro použití jednotlivých nástrojů. Můžete například vybrat z různých šířek štětců, faktorů zvětšení a stylů čáry.

Všechny nástroje, které jsou k dispozici na panelu nástrojů **Editor obrázků** , jsou také k dispozici v nabídce**nástroje**pro **Image** > . Pokud chcete použít panel nástrojů **Editor obrázků** a selektor **možností** , vyberte požadovaný nástroj nebo možnost.

![Panel nástrojů Editor obrázků](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")<br/>
Panel nástrojů **Editor obrázků**

> [!TIP]
> Když najedete kurzorem myši na tlačítko panelu nástrojů, zobrazí se popisy tlačítek. Tyto tipy vám pomůžou identifikovat funkci každého tlačítka.

Vzhledem k tomu, že mnohé z nástrojů pro kreslení jsou k dispozici z [klávesnice](../windows/accelerator-keys-image-editor-for-icons.md), někdy je užitečné skrýt panel nástrojů **Editor obrázků** .

- Chcete-li zobrazit nebo skrýt panel nástrojů **Editor obrázků** , přejděte do nabídky**panely nástrojů** **zobrazení** > a vyberte **Editor obrázků**.

> [!NOTE]
> Prvky z tohoto panelu nástrojů nebudou k dispozici, pokud soubor obrázku z aktuálního projektu nebo řešení není otevřen v **editoru obrázků**.

### <a name="option-selector"></a>přepínač možnosti

Pomocí voliče možností můžete zadat šířku čáry, tahu štětce a dalších **možností** . Ikona na tlačítku pro výběr **Možnosti** se změní v závislosti na tom, který nástroj jste vybrali.

![Vykreslení&#45;obrazce kreslení na panelu nástrojů editoru obrázků](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")<br/>
Selektor **možností** na panelu nástrojů **editoru obrázků**

### <a name="text-tool"></a>Textový nástroj

Pomocí dialogového okna **textový nástroj** můžete přidat text k prostředku kurzoru, rastrového obrázku nebo ikony.

Chcete-li získat přístup k tomuto dialogovému oknu, otevřete **Editor obrázků** a přejděte do nabídky**nástroje**pro **obrázky** > a pak vyberte příkaz **textový nástroj** .

> [!TIP]
> Můžete kliknout pravým tlačítkem myši na dialogové okno **textový nástroj** a získat přístup k výchozí místní nabídce, která obsahuje seznam standardních příkazů systému Windows.

Chcete-li změnit písmo, styl nebo velikost písma kurzoru, otevřete dialogové okno **písmo textového nástroje** . Změny se aplikují na text zobrazený v **textové** oblasti.

Chcete-li získat přístup k tomuto dialogovému oknu, vyberte tlačítko **písmo** v dialogovém okně **textový nástroj** . K dispozici jsou tyto vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Písma**|Zobrazuje dostupná písma.|
|**Styl písma**|Vypíše dostupné styly pro zadané písmo.|
|**Hodnota**|Vypisuje dostupné velikosti bodů pro zadané písmo.|
|**Vzorku**|Zobrazuje ukázku způsobu, jakým se text zobrazí se zadaným nastavením písma.|
|**skript**|Vypisuje dostupné jazykové skripty pro zadané písmo.<br/><br/>Když vyberete jiný jazykový skript, znaková sada pro tento jazyk bude k dispozici pro vytváření vícejazyčných dokumentů.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>Změna písma textu obrázku

Tady je příklad, jak přidat text do ikony v aplikaci pro Windows a manipulovat s písmem textu.

1. Vytvořte aplikaci C++ model Windows Forms. Podrobnosti najdete v tématu [How to: Vytváření aplikací](/previous-versions/visualstudio/visual-studio-2008/s69bf10x(v%3dvs.90))model Windows Forms. Ve výchozím nastavení je do projektu přidán soubor *App. ico* .

1. V **Průzkumník řešení**dvakrát klikněte na soubor *App. ico*. Otevře se **Editor obrázků** .

1. Přejděte na**nástroje** pro **obrázky** > nabídky a vyberte **textový nástroj**.

1. V dialogovém okně **textový nástroj** zadejte *C++* text do pole prázdná oblast. Tento text se zobrazí v poli umožňujícím změnu velikosti umístěnou v levém horním rohu *App. ico* v **editoru obrázků**.

1. V **editoru obrázků**přetáhněte pole pro změnu velikosti do středu *aplikace. ico* , aby se zlepšila čitelnost textu.

1. V dialogovém okně **textový nástroj** vyberte tlačítko **písmo** .

1. V dialogovém okně **písmo textového nástroje** :

   - Vyberte možnost **Times New Roman** ze seznamu dostupných písem, která jsou uvedena v poli se seznamem **písem** .

   - V seznamu dostupných stylů písem uvedených v seznamu **styl písma** vyberte **tučné** písmo.

   - V seznamu dostupných velikostí bodů uvedených v seznamu **Velikost** vyberte **10** .

   - Zvolte **OK**. Dialogové okno **písmo textového nástroje** bude zavřeno a nové nastavení písma bude platit pro váš text.

1. V dialogovém okně **textový nástroj** klikněte na tlačítko **Zavřít** . V **editoru obrázků**zmizí pole umožňující změnu velikosti kolem textu.

V oblasti textu se zobrazí text, který se zobrazí jako součást prostředku. Zpočátku je tato oblast prázdná.

> [!NOTE]
> Pokud je nastavené **průhledné pozadí** , do obrázku se umístí jenom text. Pokud je nastavené **neprůhledné pozadí** , ohraničující obdélník, vyplněný barvou pozadí, se umístí za text.

## <a name="window-panes"></a>Podokna

V okně **Editor obrázků** se zobrazí dvě zobrazení obrázku s rozděleným pruhem oddělujících dvě podokna. Můžete přetáhnout příčku ze strany na stranu, a změnit tak relativní velikosti podoken. Aktivní podokno zobrazuje hranici výběru.

Jedno zobrazení má skutečnou velikost a druhý je zvětšený o výchozí faktor zvětšení 6. Zobrazení v těchto dvou podoknech se aktualizují automaticky, všechny změny, které provedete v jednom podokně, se okamžitě zobrazí v druhém. Tato dvě podokna usnadňují práci na zvětšeném zobrazení obrázku, ve kterém můžete rozlišovat jednotlivé pixely a zároveň sledovat účinek práce na zobrazení skutečné velikosti obrázku v aktuálním čase.

V levém podokně se používá tolik místa, kolik je potřeba (až polovina okna **obrázku** ), aby se zobrazilo výchozí zobrazení 1:1 zvětšení obrázku. V pravém podokně se zobrazí výchozí obrázek zvětšení úrovně 6:1. Zvětšení v každém podokně můžete změnit pomocí nástroje **Lupa** na panelu nástrojů **editoru obrázků** nebo pomocí kláves akcelerátoru.

Můžete zvětšit menší podokno okna **Editor obrázků** a použít dvě podokna k zobrazení různých oblastí velkého obrázku. Vyberte uvnitř podokna a zvolte ho.

Relativní velikosti podoken lze změnit umístěním ukazatele myši na příčky a přesunutím příčky doprava nebo doleva. Příčka může být přesunuta na jednu stranu, pokud chcete pracovat pouze v jednom podokně.

Pokud je podokno **editoru obrázků** zvětšeno o faktor 4 nebo větší, můžete zobrazit mřížku pixelů, která odděluje jednotlivé pixely v obrázku.

### <a name="to-change-the-magnification-factor"></a>Změna faktoru zvětšení

Ve výchozím nastavení **Editor obrázků** zobrazí zobrazení v levém podokně ve skutečné velikosti a zobrazení v pravém podokně v 6 časech skutečné velikosti. Faktor zvětšení (zobrazený ve stavovém řádku v dolní části pracovního prostoru) je poměr mezi skutečnou velikostí obrázku a zobrazenou velikostí. Výchozí faktor je 6 a rozsah je od 1 do 10.

1. Vyberte podokno **editoru obrázků** , jehož faktor zvětšení chcete změnit.

1. Na panelu nástrojů **Editor obrázků** vyberte šipku napravo od nástroje **Lupa** a v podnabídce vyberte zvětšení-faktor: **1x**, **2x**, **6X**nebo **8rychlostní**.

   > [!NOTE]
   > Chcete-li vybrat jiný faktor zvětšení než ty, které jsou uvedeny v nástroji **Lupa** , použijte klávesy akcelerátoru.

### <a name="to-display-or-hide-the-pixel-grid"></a>Zobrazení nebo skrytí mřížky pixelů

Pro všechna podokna **editoru obrázků** s faktorem zvětšení 4 nebo vyšší můžete zobrazit mřížku, která odděluje jednotlivé pixely v imagi.

1. Přejděte na**Nastavení mřížky** **obrázku** > nabídky.

1. Zaškrtněte políčko **Mřížka pixelů** pro zobrazení mřížky, nebo zrušte zaškrtnutí políčka pro skrytí mřížky.

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také:

[Editory prostředků](../windows/resource-editors.md)<br/>
[Ikony](/windows/win32/menurc/icons)