---
title: Uspořádání ovládacích prvků v dialogových oknech (C++) | Dokumentace Microsoftu
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.grouping
helpviewer_keywords:
- controls [C++], positioning
- dialog box controls [C++], placement
- Dialog Editor [C++], arranging controls
- Dialog Editor [C++], guides and margins
- guides, clearing
- guides
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
- guides, disabling snapping
- controls [C++], snap to guides/grid
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
- grid spacing
- guides, settings
- layout grid in Dialog Editor
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls [C++], grouping radio buttons
- grouping controls
- radio buttons [C++], grouping on dialog boxes
- controls [C++], tab order
- focus, tab order
- tab controls [C++], tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls [C++], tab order
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
ms.openlocfilehash: 210fbf8e062b4dd8c469f9c40a015bbc19bc2843
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152739"
---
# <a name="arrangement-of-controls-on-dialog-boxes-c"></a>Uspořádání ovládacích prvků v dialogových oknech (C++)

**Dialogové okno** editor poskytuje rozložení nástroje, které Zarovnat a nastavení velikosti ovládacích prvků automaticky. Pro většinu úloh můžete použít [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Všechny **editoru dialogového okna** nástrojů příkazy jsou také k dispozici na **formátu** nabídky a většina mají [klávesových zkratek](../windows/accelerator-keys-for-the-dialog-editor.md).

Mnoho příkazů rozložení pro dialogová okna jsou k dispozici, jenom když vyberete více než jeden ovládací prvek. Můžete vybrat ovládací prvek jednoho nebo více ovládacích prvků a při výběru více než jeden ovládací prvek první z nich, kterou jste vybrali ve výchozím nastavení je "dominantního" ovládacího prvku. Další informace o výběru ovládacích prvků a dominantního ovládacího prvku, naleznete v tématu [ovládací prvky výběru](../windows/selecting-controls.md).

Umístění, výšku a šířku aktuálního ovládacího prvku se zobrazí v pravém dolním rohu stavového řádku. Při výběru celé dialogové stavový řádek zobrazuje pozice dialogových oken jako celek a jeho výška a šířka.

## <a name="dialog-editor-states-guides-and-grids"></a>Stavy editoru dialogových oken (vodítka a mřížky)

Můžete uspořádat ovládací prvky v dialogových oknech s **dialogové okno** editoru v jednom ze tří různých stavů:

- Pomocí vodítek a okrajů na (výchozí nastavení)

- Pomocí mřížky rozložení v

- Bez jakékoli funkce přichycení nebo zarovnání

[Nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) obsahuje tlačítka, která řídí stav. Chcete-li změnit stav, vyberte příslušnou položku. Můžete také změnit stavy pomocí **nastavení vodítek** příkaz **formátu** nabídky.

**Nastavení vodítek** dialogové okno má následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Vodítka rozložení**|Zobrazuje nastavení vodítek rozložení.|
|**Žádné**|Skryje nástroje rozložení.|
|**Pravítka a vodítka**|Pokud povolená, přidá do nástroje rozložení; pravítka příručky je možné použít v pravítka. Výchozí příručky jsou okraje, které je možné přesunout přetažením. Vyberte pravítka umístit průvodce. Ovládací prvky "přichytávat" k Průvodci při přesunutí ovládacích prvků nad nebo vedle sebe. Ovládací prvky se také přesunout pomocí průvodce po jste k němu připojená. Když ovládací prvek je připojen k vodítko na každé straně a přesunout vodítko, změní velikost ovládacího prvku.|
|**Mřížka**|Vytvoří rozložení mřížky. Nové ovládací prvky budou automaticky zarovnat k mřížce.|
|**Rozteč mřížky**|Nastavení pro rozteč mřížky se zobrazí v poli jednotky dialogu (dlu).|
|**Width: Dlu**|Nastavuje šířku mřížky rozložení v dlu. Vodorovné DLU je průměrná délka pole písmo dialogového okna dělený čtyři.|
|**Height: Dlu**|Nastaví výšku mřížky rozložení v dlu. Svislé DLU je průměrná výška pole písmo dialogového okna dělený osmidílné série.|

### <a name="create-and-set-guides-and-margins"></a>Vytvoření a nastavení vodítek a okrajů

Ať už přesouváte ovládací prvky, přidání ovládacích prvků nebo změna uspořádání aktuální rozložení, příručky pomáhají Zarovnat ovládací prvky přesně v rámci dialogového okna. Průvodce se zobrazí jako modré čáry s koncovými body v dialogovém okně zobrazí v editoru a odpovídající šipky v pravítka v horní části a sledovat levému okraji **dialogové okno** editoru.

Při vytváření dialogového okna, jsou k dispozici čtyři okraje. Okraje jsou upravené vodítka, povolí jako modré čáry s koncovými body.

|Proces|Kroky|
|----------------|----------------|
|Chcete-li vytvořit vodítko|V rámci pravítku vyberte po vytvoření průvodce. (Jedním kliknutím vytvoří nový průvodce; spuštění dvojitým kliknutím **nastavení vodítek** dialogovému oknu, ve kterém můžete zadat nastavení vodítek.)|
|Chcete-li nastavit vodítko|V dialogovém okně klikněte na tlačítko průvodce a přetáhněte ji na jiné místo. (Můžete také klikněte na šipku v pravítku, chcete-li přetáhněte průvodci přidružené.)<br/><br/>Souřadnice průvodce se zobrazí ve stavovém řádku v dolní části okna a pravítka. Přesunutí ukazatele myši na šipku v pravítku, chcete-li zobrazit přesné umístění v průvodci.|
|Chcete-li odstranit Průvodce|Přetáhněte z dialogových oken v průvodci.<br/><br/>\- nebo –<br/><br/>Přetáhněte šipku odpovídající vypnout pravítko.|
|Chcete-li přesunout okraje|Přetáhněte na okraji na nové místo.<br/><br/>Chcete-li okraj zmizí, přesune na okraji nulové pozice. Převést zpět na okraji, umístěte ukazatel myši na okraj nulové pozice a přesuňte do umístění na okraj.|

### <a name="align-controls-on-a-guide"></a>Zarovnání ovládacích prvků podle vodítka

Úchyty pro změnu velikosti ovládacích prvků Přichytit k vodítkům při přesunutí ovládacích prvků a příručky Přichytit k ovládací prvky, pokud neexistují žádná opatření dříve přichycená k průvodci. Když průvodce se přesune, ovládací prvky, které jsou přichycená k němu také přesunout. Ovládací prvky přichycená k více než jeden Průvodce se mění velikost, pokud jeden z příručky přesunuta.

Značky v pravítka, která určují mezery v průvodci a ovládací prvky jsou definovány jednotky dialogu (dlu). DLU vychází z velikosti pole písmo dialogového okna, obvykle 8 bodu MS Shell Dlg. Vodorovné DLU je průměrná délka pole písmo dialogového okna dělený čtyři. Svislé DLU je průměrná výška písmo dělený osmidílné série.

#### <a name="to-size-a-group-of-controls-with-guides"></a>Chcete-li velikost skupiny ovládacích prvků podle vodítka

1. Přichytit k vodítko straně ovládacího prvku (nebo ovládací prvky).

1. Přetáhněte vodítko na druhé straně ovládacího prvku (nebo ovládací prvky).

   V případě potřeby s více ovládacích prvků, velikost každého se přichytil k druhé průvodce.

1. Přesuňte buď Průvodce pro nastavení velikosti ovládacího prvku (nebo ovládací prvky).

#### <a name="to-change-the-intervals-of-the-tick-marks"></a>Chcete-li změnit intervalech osové značky

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

1. V **nastavení vodítek** v dialogu **rozteč mřížky** v dlu zadejte novou šířku a výšku.

### <a name="disable-guides"></a>Zakázání vodítek

Speciální klávesy ve spojení s myši můžete zakázat přichycení efekt vodítka. Použití **Alt** klíč zakáže přichycení efekty v průvodci vybrali. Přesunutí průvodce s **Shift** klíč zabraňuje přesunutí s příručkou Přichycený ovládací prvek.

#### <a name="to-disable-the-snapping-effect-of-the-guides"></a>Chcete-li zakázat přichycení efekt vodítka

Přetáhněte ovládací prvek při podržení **Alt** klíč.

#### <a name="to-move-guides-without-moving-the-snapped-controls"></a>Chcete-li přesunout vodítka bez přesouvání Přichycený ovládací prvky

Přetáhněte vodítko při podržení **Shift** klíč.

#### <a name="to-turn-off-the-guides"></a>Chcete-li vypnout vodítka

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

1. V **nastavení vodítek** dialogovém okně **vodítka rozložení**vyberte **žádný**.

   > [!NOTE]
   > Můžete také dvakrát kliknout na panelu pravítko pro přístup k **nastavení vodítek** dialogové okno.

\- nebo –

Na **formátu** nabídce vyberte možnost **průvodce přepínací tlačítko**.

### <a name="modify-the-layout-grid"></a>Změna mřížky rozložení

Při uvádění nebo uspořádání ovládacích prvků v dialogovém okně, můžete pro přesnější umístění rozložení mřížky. Po zapnutí mřížky "se přichytil k" tečkované čáry mřížky jakoby zmagnetizovat zobrazí ovládací prvky. Můžete zapnout a vypnout tuto funkci "přichycení k mřížce" a změnit velikost buňky mřížky rozložení.

#### <a name="to-turn-the-layout-grid-on-or-off"></a>K zapnutí nebo vypnutí mřížky rozložení

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

1. V **nastavení vodítek** dialogové okno, zaškrtněte nebo zrušte **mřížky** tlačítko.

   Můžete řídit mřížky v jednotlivých **dialogové okno** oken editoru pomocí **Přepnout mřížku** tlačítko [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

#### <a name="to-change-the-size-of-the-layout-grid"></a>Chcete-li změnit velikost rozložení mřížky

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

1. V **nastavení vodítek** dialogového okna zadejte výšku a šířku v dlu buňky v mřížce. Minimální výšku nebo šířku je 4 dlu.

## <a name="group-radio-buttons-on-a-dialog-box"></a>Skupiny přepínačů v dialogovém okně

Při přidání přepínacích tlačítek do dialogového okna s nimi zacházet jako se skupinou tak, že nastavíte **skupiny** vlastnost **vlastnosti** okno pro první tlačítka ve skupině. ID ovládacího prvku pro tento přepínač se pak objeví v [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md), abyste mohli přidat členskou proměnnou pro skupinu přepínačů.

Můžete mít více než jedné skupině přepínačů v dialogovém okně a každá skupina by se měl přidat pomocí následujícího postupu.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Do dialogového okna Přidat skupinu přepínačů

1. Vyberte ovládací prvek přepínač tlačítko v [okno nástrojů](/visualstudio/ide/reference/toolbox) a vyberte umístění v dialogovém okně místo, kam chcete umístit ovládací prvek.

1. Zopakujte krok 1 pro přidání tolika přepínačů, podle potřeby. Ujistěte se, že jsou v pořadí po sobě jdoucích přepínací tlačítka ve skupině.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), nastavte **skupiny** vlastnost *první* přepínač v pořadí karet na **True**.

   Změna **skupiny** vlastnost **True** přidá WS_GROUP styl tlačítka položky v objektu dialogového okna skriptu, prostředků a zajistí, že uživatel zvolit pouze jeden přepínací tlačítko současně na tlačítku skupiny (když uživatel klikne jeden přepínací tlačítko, ostatní ve skupině jsou vymazány).

   > [!NOTE]
   > Pouze první přepínací tlačítko ve skupině by měly mít **skupiny** vlastnost nastavena na hodnotu **True**. Pokud máte další ovládací prvky, které nejsou součástí skupiny tlačítko, nastavte **skupiny** vlastnost první ovládací prvek *, která je mimo skupinu* k **True** také. Můžete rychle identifikovat první ovládací prvek mimo skupinu stisknutím kombinace kláves **Ctrl**+**D** Chcete-li zobrazit pořadí ovládacích prvků.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Přidání členské proměnné pro skupina přepínacích tlačítek

1. Klikněte pravým tlačítkem na první tlačítko ovládacím prvku přepínač v pořadí (dominantního ovládacího prvku a ten se **skupiny** nastavenou na hodnotu True).

1. Zvolte **přidat proměnnou** z místní nabídky.

1. V [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md), vyberte **řídicí proměnná** zaškrtněte políčko a potom vyberte **hodnotu** přepínač.

1. V **název proměnné** zadejte název pro novou proměnnou člena.

1. V **typ proměnné** pole se seznamem, vyberte **int** nebo typ `int`.

1. Nyní můžete upravit kódu k určení, jaké tlačítko přepínače by se měla zobrazit vybraný. Například `m_radioBox1 = 0;` vybere první přepínací tlačítko ve skupině.

## <a name="align-groups-of-controls"></a>Zarovnání skupin ovládacích prvků

Následující postupy ukazují, jak Zarovnat ovládací prvky:

### <a name="to-align-groups-of-controls"></a>Zarovnání skupin ovládacích prvků

1. [Vyberte ovládací prvky](../windows/selecting-multiple-controls.md) chcete zarovnat. Vyberte ovládací prvek, který se má provádět dominantního ovládacího prvku nebo nastavit tak, aby se dominantního ovládacího prvku před provádění zarovnání nebo změny velikosti příkazu.

   Konečná pozice skupiny ovládacích prvků, závisí na pozici dominantního ovládacího prvku. Další informace o výběru dominantního ovládacího prvku, naleznete v tématu [určení dominantního ovládacího prvku](../windows/specifying-the-dominant-control.md).

1. Z **formátu** nabídce zvolte **zarovnat**a pak vyberte jednu z následujících zarovnání:

   - `Lefts`: Zarovná vybrané ovládací prvky jejich levé strany.

   - `Centers`: Zarovná vybrané ovládací prvky vodorovně jejich bodů System center.

   - `Rights`: Zarovná vybrané ovládací prvky jejich pravé straně.

   - `Tops`: Zarovná vybrané ovládací prvky jeho horní hrany.

   - `Middles`: Zarovná vybrané ovládací prvky svisle podél jejich střední body.

   - `Bottoms`: Zarovná vybrané ovládací prvky dolního okraje.

### <a name="to-even-the-spacing-between-controls"></a>Dodavatelské mezer mezi ovládacími prvky

**Dialogové okno** editor umožňuje ovládacích prvků místo rovnoměrně mezi nejkrajnější vybraných ovládacích prvků.

1. Vyberte ovládací prvky, které chcete změnit uspořádání.

1. Z **formátu** nabídce zvolte **místo rovnoměrně**a pak vyberte jednu z následujících zarovnání mezery:

   - `Across`: místo ovládacích prvků rovnoměrně mezi první a poslední ovládací prvek.

   - `Down`: místo ovládacích prvků rovnoměrně mezi horní a nejspodnějších ovládací prvek.

### <a name="to-center-controls-in-a-dialog-box"></a>Zarovnat na střed ovládacích prvků v dialogovém okně

1. Vyberte ovládací prvek nebo prvky, které chcete změnit uspořádání.

1. Z **formátu** nabídce zvolte **Center v dialogovém okně**a pak vyberte jednu z následujících opatření:

   - `Vertical`: střed ovládacích prvků v dialogovém okně svisle.

   - `Horizontal`: střed ovládacích prvků v dialogovém okně vodorovně.

### <a name="to-arrange-push-buttons-along-the-right-or-bottom-of-a-dialog-box"></a>Uspořádání tlačítek podél pravé nebo dolní části dialogového okna

1. Vyberte jeden nebo více tlačítek.

1. Z **formátu** nabídce zvolte **uspořádat tlačítka**a pak vyberte jednu z následujících opatření:

   - `Right`: zarovná tlačítek podél pravého okraje dialogového okna.

   - `Bottom`: zarovná tlačítek podél dolního okraje dialogového okna.

       Pokud vyberete ovládací prvek než příkazové tlačítko, jeho pozice nemá vliv.

## <a name="change-the-tab-order-of-controls"></a>Změna pořadí ovládacích prvků

Pořadí, ve kterém je pořadí **kartu** klíč přesune zaměření pro vstup z jednoho ovládacího prvku v rámci dialogového okna. Obvykle pokračuje pořadí zleva doprava a shora dolů v dialogovém okně. Každý ovládací prvek má **Tabstop** vlastnost, která určuje, zda ovládací prvek nastaven vstupní fokus.

### <a name="to-set-input-focus-for-a-control"></a>Chcete-li nastavit fokus vstupu pro ovládací prvek

V [okno vlastností](/visualstudio/ide/reference/properties-window)vyberte **True** nebo **False** v **Tabstop** vlastnost.

Dokonce i ovládací prvky, které nemají **Tabstop** nastavenou na **True** musí být součástí pořadí ovládacích prvků. Pořadí je důležité, například, když jste [definujte přístupové klíče (klávesových zkratek)](../windows/defining-mnemonics-access-keys.md) pro ovládací prvky, které nemají titulky. Statický text, který obsahuje přístupový klíč pro související ovládací prvek musí bezprostředně předcházet související ovládací prvek v pořadí.

> [!NOTE]
> Pokud vaše dialogové okno obsahuje překrývající se ovládací prvky, změna pořadí karet může změnit způsob, jakým se zobrazí ovládací prvky. Ovládací prvky, které jsou dále v pořadí karet se vždy zobrazují nad překrývající se ovládací prvky, které předcházet v pořadí.

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Chcete-li zobrazit aktuální pořadí pro všechny ovládací prvky v dialogovém okně

Na **formátu** nabídce vyberte možnost **pořadí**.

\- nebo –

- Stisknutím klávesy **Ctrl** + **D**.

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Chcete-li změnit pořadí ovládacích prvků pro všechny ovládací prvky v dialogovém okně

1. Na **formátu** nabídce vyberte možnost **pořadí**.

   Řadu každý ovládací prvek v levém horním rohu se zobrazí místo něj v aktuální pořadí.

1. Nastavení pořadí karet klikněte na každý prvek v pořadí, které chcete **kartu** klíč použít.

1. Stisknutím klávesy **Enter** ukončíte **pořadí** režimu.

   > [!TIP]
   > Jakmile zadáte **pořadí** režimu, můžete stisknout **Esc** nebo **Enter** zakázat možnost změnit pořadí ovládacích prvků.

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Chcete-li změnit pořadí pro dva nebo více ovládacích prvků

1. Z **formátu** nabídce zvolte **pořadí**.

1. Zadejte, kde se začne změna v pořadí. Podržte stisknutou klávesu nejprve **Ctrl** klíče a vyberte ovládací prvek a pak vyberte ten, kde chcete začít změněné směr.

   Například, pokud chcete změnit pořadí ovládacích prvků `7` prostřednictvím `9`, podržte stisknutou klávesu **Ctrl**, vyberte ovládací prvek `6` první.

   > [!NOTE]
   > Chcete-li nastavit konkrétní ovládací prvek na číslo `1` (první v pořadí), poklepejte na ovládací prvek.

1. Verze **Ctrl** klíče a potom vyberte ovládací prvky v pořadí, které chcete **kartu** klíč dodržovat od tohoto okamžiku.

1. Stisknutím klávesy **Enter** ukončíte **pořadí** režimu.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)