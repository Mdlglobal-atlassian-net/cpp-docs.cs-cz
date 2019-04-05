---
title: 'Postupy: Pracovat s barvou'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.color
- vc.editors.customcolorselector
- vc.editors.loadcolorpalette
- vc.editors.colorswindow
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors [C++], Image editor
- colors [C++]
- Image editor [C++], colors
- colors [C++], Image editor
- colors [C++], image
- images [C++], colors
- Image editor [C++], colors
- Fill tool
- colors [C++], image
- images [C++], colors
- colors [C++], selection tools
- Image editor [C++], colors
- Select Color tool
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
- Image editor [C++], Colors Palette
- Colors Palette, Image editor
- colors [C++], inverting
- colors [C++]
- Color Indicator
- colors [C++], Colors window
- Colors window, hiding colors
- Show Colors Window command
- Colors window, displaying colors
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
- opaque backgrounds [C++]
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- images [C++], transparency
- images [C++], opaque background
- colors [C++], image
- Image editor [C++], color inversion
- images [C++], colors
- colors [C++], inverting
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
ms.openlocfilehash: c424d2e613c51f901def13c4bf42a066797cc65c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034141"
---
# <a name="how-to-work-with-color"></a>Postupy: Pracovat s barvou

**Editor obrázků** obsahuje řadu funkcí, které konkrétně zpracování a přizpůsobení barev. Můžete nastavit barvu popředí nebo pozadí, vyplnění ohraničené oblasti barvou nebo vybrat barvu na obrázku, který má použít jako aktuální barvu popředí nebo pozadí. Pomocí nástrojů v [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) spolu s palety barev v **barvy** okno pro vytvoření bitové kopie.

Všechny barvy pro monochromatický a 16 barev obrázků jsou uvedeny v **barvy** paletu **barvy** okna. Spolu s 16 standardní barvy můžete vytvořit své vlastní barvy. Změna barev v paletě okamžitě změnit odpovídající barvu v obrázku.

Při práci s 256 barvami ikonu a obrázky kurzor **barvy** vlastnost v [okno vlastností](/visualstudio/ide/reference/properties-window) se používá. Další informace najdete v tématu [vytváření 256barevných ikony nebo kurzoru s](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md).

Můžete také vytvořit Image true color. Však nejsou zobrazeny true color ukázky úplné paletě v **barvy** okno; zobrazí se pouze v oblasti indikátor barvy popředí nebo pozadí. True barvy se vytvoří s použitím **výběr vlastní barvy** dialogové okno.

Můžete uložit vlastní barvy palety na disku a načítat je znovu podle potřeby. Palety barev, které jste naposledy použili je uložen v registru a automaticky načte při dalším spuštění sady Visual Studio.

**Barvy** okno má dvě části:

- **Barvy palety**, což je pole vzorky barev, které představují barvy, které můžete použít. Ukázky a zvolte barvy popředí a pozadí, pokud používáte nástroje grafiky můžete vybrat.

- **Indikátor barvy**, který zobrazuje barvy popředí a pozadí a selektory obrazovky a inverzní barvy.

   ![Okno barvy](../windows/media/vccolorswindow.gif "vcColorsWindow")<br/>
   **Barvy** okna

> [!NOTE]
> **Barvu obrazovky** a **inverzní barvy** nástroje jsou dostupné jenom pro ikony a kurzory.

Můžete použít **barvy** okna [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md).

- Pro zobrazení **barvy** okna, klikněte pravým tlačítkem v **Editor obrázků** podokně a zvolte **zobrazit okno barev**, nebo přejděte do nabídky [Image](../windows/image-menu-image-editor-for-icons.md)  >  **Zobrazit okno barev**.

- Chcete-li skrýt **barvy** okna, Odepnout okno (Tato akce umožní okna automatické skrývání až nebude používán) nebo vyberte **Zavřít** tlačítko.

**Barvy** otevření zobrazí standardní 16 barev palety. Zobrazené barvy můžete také vytvořit vlastní barvy. Pak můžete uložit a načíst vlastní paletu barev.

**Výběr vlastní barvy** dialogové okno umožňuje přizpůsobit barvy, můžete použít pro vaši image s následujícími vlastnostmi:

|Vlastnost|Popis|
|--------------------------|--------------------------|
|**Barevný přechod zobrazení**|Změní hodnoty vybraná barva.<br/><br/>Umístěte na křížek na barvu, kterou chcete změnit a přesuňte posuvník nahoru nebo dolů můžete změnit světelnost nebo hodnoty RGB barvy.|
|**Panel světelnost**|Nastaví světelnost pro barvu vyberte v **přechodu barevné zobrazení** pole.<br/><br/>Vyberte a přetáhněte bílé šipka nahoru na panelu pro větší jas nebo méně. **Barva** zobrazí vámi zvolená barva a účinnosti světelnost nastavíte.|
|**Barva**|Zobrazí seznam (hodnota barvy kolečko) odstín barvy, které definujete. Hodnoty v rozsahu od 0 do 240, kde 0 je červené, 60 je žlutý, je 120 zelená, 180 je azurová, 200 je purpurová a 240 je modrá.|
|**HUE**|Zobrazí seznam (hodnota barvy kolečko) odstín barvy, které definujete. Hodnoty v rozsahu od 0 do 240, kde 0 je červené, 60 je žlutý, je 120 zelená, 180 je azurová, 200 je purpurová a 240 je modrá.|
|**Po Ne**|Určuje hodnotu sytost barev, které definujete. Sytost je množství barvy v zadané odstín. Hodnoty v rozmezí 0 až 240.|
|**Světelnost**|Zobrazí seznam světelnost (jas) barvy, které definujete. Hodnoty v rozmezí 0 až 240.|
|**Červená**|Určuje červená barva, kterou definujete. Hodnoty v rozsahu od 0 do 255.|
|**Zelená**|Určuje hodnotu zelenou barvu, kterou definujete. Hodnoty v rozsahu od 0 do 255.|
|**Modrá**|Určuje modré hodnotu barvy, které definujete. Hodnoty v rozsahu od 0 do 255.|

Můžete uložit a načíst **barvy** paletu, která obsahuje vlastní barvy. Ve výchozím nastavení **barvy** palety naposledy použité se vyplní automaticky, když spustíte Visual Studio.

> [!TIP]
> Protože **Editor obrázků** nemá žádný způsob, jak obnovit výchozí **barvy** palety, měli byste uložit výchozí **barvy** palety pod názvem, jako  *Standard.PAL* nebo *default.pal* tak, aby je snadno obnovit výchozí nastavení.

Použít **načíst barvy palety** dialogové okno Načíst palet barev speciální pro použití v projektu v jazyce C++ s následujícími vlastnostmi:

|Vlastnost|Popis|
|-----------------|-----------------|
|**Oblast hledání**|Určuje umístění, ve které chcete najít soubor nebo složku.<br/><br/>Vyberte šipku a vybrat jiné umístění nebo vyberte ikonu složky na panelu nástrojů pro posun úrovně výš.|
|**Název souboru**|Poskytuje prostor pro zadání názvu souboru, který chcete otevřít.<br/><br/>Pokud chcete rychle vyhledat soubor, který jste dříve otevřeli, vyberte název souboru v rozevíracím seznamu, pokud je k dispozici.<br/><br/>Pokud hledáte souboru, můžete použít hvězdičky (*) jako zástupné znaky. Například můžete zadat \*.\* zobrazíte seznam všech souborů. Můžete také zadat úplnou cestu k souboru, například *C:\My Documents\MyColorPalette.pal* nebo  *\\\NetworkServer\MyFolder\MyColorPalette.pal*.|
|**Soubory typu**|Seznam typů souborů, které se zobrazí.<br/><br/>Paleta (* .pal) je výchozí typ souboru pro palet barev.|

## <a name="how-to"></a>Postupy

### <a name="to-select-foreground-or-background-colors"></a>Pro výběr barev popředí nebo pozadí

S výjimkou **gumy**, nástroje na **Editor obrázků** draw nástrojů s aktuální barvu popředí nebo pozadí při stisknutí tlačítka myši doleva nebo doprava, v uvedeném pořadí.

- Vyberte barvu popředí s levým tlačítkem myši, vyberte na požadovanou barvu **barvy** palety.

- Vybrat barvu pozadí s pravým tlačítkem myši, vyberte na požadovanou barvu **barvy** palety.

### <a name="to-fill-a-bounded-area-of-an-image-with-a-color"></a>Vyplnění ohraničené oblasti obrázku barvou

**Editor obrázků** poskytuje **vyplnit** nástroj pro naplnění všechny uzavřené oblast obrázku s aktuální vykreslení barvy nebo aktuální barvu pozadí.

### <a name="to-use-the-fill-tool"></a>Použití nástroje výplně

1. Použití **Editor obrázků** nástrojů nebo přejděte do nabídky **Image** > **nástroje** a vyberte **vyplnit** nástroj.

1. V případě potřeby vyberte vykreslení barvy. V [barvy palety](../windows/colors-window-image-editor-for-icons.md), vyberte levé tlačítko myši pro výběr barev popředí nebo na tlačítko pravým tlačítkem myši a vyberte barvu pozadí.

1. Přesunout **výplně** nástroj k oblasti, které chcete vyplnit.

1. Vyberte tlačítko myši doleva nebo doprava naplnění barvu popředí nebo pozadí.

### <a name="to-pick-up-a-color-from-an-image-to-use-elsewhere"></a>Aby se získaly barvy z obrázku použít jinde

**Vyberte barvu**, nebo barva vyzvednutí, nástroj vytvoří libovolnou barvu na obrázku aktuální barvu popředí nebo pozadí, v závislosti na tom, zda stisknutím levé nebo pravé tlačítko myši. Chcete-li zrušit **vyberte barvu** nástroj, zvolte jiný nástroj.

1. Použití **Editor obrázků** nástrojů nebo přejděte do nabídky **Image** > **nástroje** a vyberte **vyberte barvu** nástroj.

1. Vyberte barvu, kterou chcete vybrat z této image.

   > [!NOTE]
   > Po výběru barvy, **Editor obrázků** znovu aktivuje naposledy použité nástroj.

1. Kreslení pomocí levé tlačítko myši pro barvu popředí nebo pravé tlačítko myši pro barvu pozadí.

### <a name="to-choose-the-background"></a>Chcete-li zvolit na pozadí

Při přesunutí nebo kopírování výběru z bitové kopie, žádné pixelech ve výběru, které odpovídají barvě pozadí jsou ve výchozím nastavení transparentní a že není skryl pixelů v cílovém umístění.

Můžete přepnout z průhledné pozadí (výchozí) do neprůhledné pozadí a zpět. Při použití nástroje pro výběr, **průhledné pozadí** a **neprůhledné pozadí** možnosti se zobrazí **možnost** selektor na **Editor obrázků** nástrojů.

![Možnosti pozadí &#45; neprůhledné nebo průhledné](../windows/media/vcimageeditoropaqtranspback.gif "možnosti pozadí &#45; neprůhledné nebo průhledné")<br/>
**Možnosti transparentní a neprůhledné** na **panelu nástrojů editoru obrázků**

#### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Chcete-li přepnout mezi transparentní a neprůhledné pozadí

V **Editor obrázků** nástrojů, vyberte **možnost** pro výběr a klikněte na tlačítko na pozadí odpovídající:

- **Neprůhledné pozadí (O)**: Existující bitová kopie je skryté ve všech částech výběru.

- **Průhledné pozadí (T)**: Existující obrázek ukazuje prostřednictvím částí výběru, které odpovídají barvě pozadí.

> [!TIP]
> Pro místní v **Image** nabídky, zaškrtněte nebo zrušte **kreslení neprůhledných**.

Při výběru je již platná, chcete-li změnit, které části obrázku je transparentní, můžete změnit barvu pozadí.

### <a name="to-invert-the-colors-in-a-selection"></a>K invertování barev ve výběru

**Editor obrázků** poskytuje pohodlný způsob, jak Invertovat barvy ve vybrané části obrázku tak poznáte podle zobrazení obrázku s obráceným barvami.

Invertovat barvy v aktuálním výběru, přejděte do nabídky **Image** > **Invertovat barvy**.

### <a name="to-customize-or-change-colors-on-the-colors-palette"></a>K přizpůsobení nebo změna barev v paletě barvy

1. Přejděte do nabídky **Image** > **přizpůsobit barvy**.

1. V **výběr vlastní barvy** dialogového okna, definovat barvu tak, že zadáte hodnoty vyjadřující příslušná textová pole nebo jejich výběr barvy v **přechodu barevné zobrazení** pole.

1. Nastavte světelnost přesunutím posuvníku **světelnost** panelu.

1. Jsou rozloženy mnoho vlastních barev. Pokud chcete plnou barvu nejblíže tónovaná barva, dvakrát klikněte **barva** pole.

   Pokud se později rozhodnete, chcete, aby tónovaná barva, nastavte posuvník **světelnost** pruhu nebo přesunutí mezi vlasy v **přechodu barevné zobrazení** obnovíte rozklad pole.

1. Vyberte **OK** přidáte novou barvu.

### <a name="to-save-a-custom-colors-palette"></a>Chcete-li uložit vlastní barvy palety

1. Přejděte do nabídky **Image** > **Uložit paletu**.

1. Přejděte do adresáře, kam chcete uložit paletu a zadejte název pro paletě.

1. Vyberte **Uložit**.

### <a name="to-load-a-custom-colors-palette"></a>Načíst vlastní barvy palety

1. Přejděte do nabídky **Image** > **načíst paletu**.

1. V **načíst barvy palety** dialogové okno, přejděte na správný adresář a vyberte paletu chcete načíst. **Barva** palety se uloží s příponou souboru .pal.

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také:

[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)<br/>
[Postupy: Vytvoření ikony nebo jiného obrázku](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Postupy: Upravit obrázek](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Postupy: Použití nástroje kreslení](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
