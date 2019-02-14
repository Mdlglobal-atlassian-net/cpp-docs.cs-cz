---
title: Uspořádání ovládacích prvků v dialogových oknech (C++) | Dokumentace Microsoftu
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.grouping
- vc.editors.dialog.combo
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
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
ms.openlocfilehash: 99667898428fe9532d59277bfedafd24927304dc
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264878"
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

Chcete-li velikost skupiny ovládacích prvků podle vodítka:

1. Přichytit k vodítko straně ovládacího prvku (nebo ovládací prvky).

1. Přetáhněte vodítko na druhé straně ovládacího prvku (nebo ovládací prvky).

   V případě potřeby s více ovládacích prvků, velikost každého se přichytil k druhé průvodce.

1. Přesuňte buď Průvodce pro nastavení velikosti ovládacího prvku (nebo ovládací prvky).

Chcete-li změnit intervalech osové značky:

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

1. V **nastavení vodítek** v dialogu **rozteč mřížky** v dlu zadejte novou šířku a výšku.

### <a name="disable-guides"></a>Zakázání vodítek

Speciální klávesy ve spojení s myši můžete zakázat přichycení efekt vodítka. Použití **Alt** klíč zakáže přichycení efekty v průvodci vybrali. Přesunutí průvodce s **Shift** klíč zabraňuje přesunutí s příručkou Přichycený ovládací prvek.

- Zakázat přichycení efekt vodítka, přetáhněte ovládací prvek při podržení **Alt** klíč.

- Pokud chcete přesunout vodítka bez přesouvání Přichycený ovládací prvky, přetáhněte v Průvodci při podržení **Shift** klíč.

- Chcete-li vypnout vodítka, z **formátu** nabídce zvolte **nastavení vodítek**. Pak v **nastavení vodítek** dialogovém okně **vodítka rozložení**vyberte **žádný**.

   > [!NOTE]
   > Můžete také dvakrát kliknout na panelu pravítko pro přístup k **nastavení vodítek** dialogové okno.

> [!TIP]
> Je zástupce vypnout vodítka na **formátu** nabídce vyberte možnost **průvodce přepínací tlačítko**.

### <a name="modify-the-layout-grid"></a>Změna mřížky rozložení

Při uvádění nebo uspořádání ovládacích prvků v dialogovém okně, můžete pro přesnější umístění rozložení mřížky. Po zapnutí mřížky "se přichytil k" tečkované čáry mřížky jakoby zmagnetizovat zobrazí ovládací prvky. Můžete zapnout a vypnout tuto funkci "přichycení k mřížce" a změnit velikost buňky mřížky rozložení.

Chcete-li mřížky rozložení zapnutí nebo vypnutí:

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

1. V **nastavení vodítek** dialogové okno, zaškrtněte nebo zrušte **mřížky** tlačítko.

   Můžete řídit mřížky v jednotlivých **dialogové okno** oken editoru pomocí **Přepnout mřížku** tlačítko [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Chcete-li změnit velikost rozložení mřížky:

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

1. V **nastavení vodítek** dialogového okna zadejte výšku a šířku v dlu buňky v mřížce. Minimální výšku nebo šířku je 4 dlu.

## <a name="selecting-controls"></a>Výběr ovládacích prvků

Vyberte ovládací prvky na velikost, zarovnání, přesunutí, kopírování, nebo je odstranit a dokončete operaci, kterou chcete. Ve většině případů je třeba vybrat více než jeden ovládací prvek při použití nástroje pro velikost a zarovnání na [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Při výběru ovládacího prvku, má šedé ohraničení kolem něj plný (aktivní) nebo prázdný (neaktivní) "úchyty," squares malý, který se zobrazí v ohraničení výběru. Když vyberete více ovládacích prvků, dominantního ovládacího prvku má solid úchyty a všechny ostatní vybrané ovládací prvky mají prázdný úchyty.

Při nastavování velikosti nebo zarovnání více ovládacích prvků **dialogové okno** editor používá "dominantního ovládacího prvku" zjistit, jak se ostatní ovládací prvky velikosti nebo zarovnána. Ve výchozím nastavení dominantní ovládací prvek je první ovládací prvek.

### <a name="to-select-multiple-controls"></a>Výběr více ovládacích prvků

1. V [okno nástrojů](/visualstudio/ide/reference/toolbox), vyberte **ukazatel** nástroj.

1. Svůj výběr použijte jednu z následujících kroků:

   - Tažením nakreslete rámeček výběru okolo ovládací prvky, které chcete vybrat ve vašem dialogovém okně. Když uvolníte tlačítko myši, všechny řídí uvnitř a protínající se operátory jsou vybrané pole výběru.

   - Podržte stisknutou klávesu **Shift** klíče a vyberte ovládací prvky, které chcete zahrnout do výběru.

   - Podržte stisknutou klávesu **Ctrl** klíče a vyberte ovládací prvky, které chcete zahrnout do výběru.

### <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>Odebrat ovládací prvek ze skupiny z vybraných ovládacích prvků nebo přidání ovládacího prvku na skupinu vybraných ovládacích prvků

Se skupinou vybraných ovládacích prvků, podržte stisknutou klávesu **Shift** klíče a vyberte ovládací prvek, který chcete odstranit nebo přidat do existujícího výběru.

   > [!NOTE]
   > Podržení **Ctrl** klíč a výběru ovládacího prvku Výběr způsobí, že, které řídí dominantního ovládacího prvku v tomto výběru.

### <a name="to-specify-the-dominant-control"></a>K určení dominantního ovládacího prvku

Podržte stisknutou klávesu **Ctrl** klíče a vyberte ovládací prvek, kterou chcete použít k ovlivnění velikosti či umístění jiných ovládacích prvků *první*.

> [!NOTE]
> Úchyty dominantního ovládacího prvku jsou pořádné popisovače podřízených ovládacích prvků, které jsou prázdné. Všechny další změny velikosti nebo zarovnání podle dominantního ovládacího prvku.

### <a name="to-change-the-dominant-control"></a>Chcete-li změnit dominantního ovládacího prvku

1. Zrušte aktuální výběr kliknutím mimo všechny aktuálně vybrané ovládací prvky.

1. Opakujte předchozí postup nejprve výběr jiného ovládacího prvku.

## <a name="sizing-controls"></a>Změna velikosti ovládacích prvků

Použijte úchyty pro změnu velikosti ovládacího prvku. Pokud je ukazatel myši umístěn na úchyt pro změnu velikosti, změní tvar, který má označení směry, ve kterých můžete změnit velikost ovládacího prvku. Aktivní úchyty jsou pořádné; Pokud je dutý úchyt pro změnu velikosti, ovládací prvek nelze změnit velikost podél osy.

Můžete také změnit velikost ovládacího prvku pomocí přichycení vodítka a okraje ovládacího prvku, nebo přesunutím jeden přichycené zobrazení ovládacího prvku a Průvodce mimo jiné.

### <a name="to-size-an-individual-control"></a>Pro nastavení velikosti jednotlivé ovládací prvky

1. Vyberte ovládací prvek.

1. Přetažením úchytů změňte velikost ovládacího prvku:

   - Úchyty pro změnu velikosti na začátku a konce změnit velikost vodorovně nebo svisle.

   - Úchyty pro změnu velikosti v rozích změnit šířku a výšku.

   > [!TIP]
   > Můžete změnit velikost jednotky jeden dialogového okna ovládacího prvku (DLU) současně současným **Shift** klíče a pomocí **šipka vpravo** a **šipka dolů** klíče.

### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Chcete-li automaticky velikost ovládacího prvku podle textu v rámci něj

Zvolte **velikost, aby se obsah** z **formátu** nabídku nebo klikněte pravým tlačítkem na ovládací prvek a vyberte **velikost obsahu** z místní nabídky.

### <a name="to-make-controls-the-same-width-height-or-size"></a>Aby se řídí stejnou šířku, výšku ani velikost

Změnit velikost skupiny ovládacích prvků na základě velikosti dominantního ovládacího prvku.

1. Vyberte ovládací prvky, které chcete změnit velikost.

   Ovládací prvek nejprve v řadě je dominantního ovládacího prvku. Konečné velikosti ovládacích prvků ve skupině závisí na velikosti dominantního ovládacího prvku.

1. Z **formátu** nabídce zvolte **nastavit stejnou velikost**, klikněte na tlačítko **obě**, **výška**, nebo **šířka**.

### <a name="to-set-the-size-of-the-combo-box-and-its-drop-down-list"></a>K nastavení velikosti pole se seznamem pole a jeho rozevíracího seznamu

Při přidání do dialogových oken, můžete měnit velikost pole se seznamem. Můžete také určit velikost pole rozevíracího seznamu. Další informace najdete v tématu [přidání hodnot do ovládacího prvku pole se seznamem](../windows/adding-values-to-a-combo-box-control.md).

#### <a name="to-size-a-combo-box"></a>Pro nastavení velikosti pole se seznamem

1. Vyberte ovládací prvek pole se seznamem ve vašem dialogovém okně.

   Na začátku jsou aktivní pouze vpravo a vlevo úchyty.

1. Pomocí úchytů nastavte šířku pole se seznamem.

Můžete také nastavit velikost svislé rozbalovaná část pole se seznamem.

#### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>Nastavení velikosti pole se seznamem pole rozevíracího seznamu

1. Vyberte tlačítko se šipkou rozevíracího seznamu na pravé straně pole se seznamem.

   ![Šipka na pole se seznamem v projektu knihovny MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Přehled ovládacího prvku změn zobrazíte velikost pole se seznamem s rozevíracího seznamu oblastí extended.

1. Chcete-li změnit počáteční velikost oblasti rozevíracího seznamu použijte dolní úchyt pro změnu velikosti.

   ![Pole se seznamem&#45;nastavení velikosti pole v projektu knihovny MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Vyberte šipku rozevíracího seznamu zavřete rozevírací část pole se seznamem.

### <a name="to-set-the-width-of-a-horizontal-scroll-bar-and-make-it-appear"></a>Nastavení šířky vodorovného posuvníku a usnadnit zobrazí

Když přidáte seznam s vodorovný posuvník do dialogového okna pomocí tříd knihovny MFC, posuvník nezobrazí automaticky ve vaší aplikaci.

Nastavte maximální šířku prvku nejširší voláním [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) ve vašem kódu.

   Bez této sady hodnot posuvník nezobrazí, i když jsou položky v seznamu širší než pole.

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

## <a name="to-align-groups-of-controls"></a>Zarovnání skupin ovládacích prvků

1. Vyberte ovládací prvky, které chcete, aby bylo v souladu. Vyberte ovládací prvek, který se má provádět dominantního ovládacího prvku nebo nastavit tak, aby se dominantního ovládacího prvku před provádění zarovnání nebo změny velikosti příkazu.

   Konečná pozice skupiny ovládacích prvků, závisí na pozici dominantního ovládacího prvku. Další informace o výběru dominantního ovládacího prvku, naleznete v tématu [určení dominantního ovládacího prvku](../windows/specifying-the-dominant-control.md).

1. Z **formátu** nabídce zvolte **zarovnat**a pak vyberte jednu z následujících zarovnání:

   |Hodnota|Popis|
   |-----|-----------|
   |`Lefts`|Zarovná vybrané ovládací prvky jejich levé strany.|
   |`Centers`|Zarovná vybrané ovládací prvky vodorovně jejich bodů System center.|
   |`Rights`|Zarovná vybrané ovládací prvky jejich pravé straně.|
   |`Tops`|Zarovná vybrané ovládací prvky jeho horní hrany.|
   |`Middles`|Zarovná vybraných ovládacích prvků svisle podél jejich střední body.|
   |`Bottoms`|Zarovná vybrané ovládací prvky dolního okraje.|

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

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)