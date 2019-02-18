---
title: 'Postupy: Uspořádání ovládacích prvků (C++) | Dokumentace Microsoftu'
ms.date: 02/15/2019
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
ms.openlocfilehash: d9bd73c9cc81b113f222bbc090c62200c93554b2
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336628"
---
# <a name="how-to-arrange-controls-c"></a>Postupy: Uspořádání ovládacích prvků (C++)

**Dialogové okno** editor poskytuje rozložení nástroje, které Zarovnat a nastavení velikosti ovládacích prvků automaticky. Pro většinu úloh můžete použít [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Všechny **editoru dialogového okna** nástrojů příkazy jsou také k dispozici na **formátu** nabídky a většina mají [klávesových zkratek](../windows/accelerator-keys-for-the-dialog-editor.md).

Mnoho příkazů rozložení pro dialogová okna jsou k dispozici, jenom když vyberete více než jeden ovládací prvek. Můžete vybrat ovládací prvek jednoho nebo více ovládacích prvků a při výběru více než jeden ovládací prvek první z nich, kterou jste vybrali ve výchozím nastavení je "dominantního" ovládacího prvku. Další informace o výběru ovládacích prvků a dominantního ovládacího prvku, naleznete v tématu [ovládací prvky výběru](../windows/selecting-controls.md).

Umístění, výšku a šířku aktuálního ovládacího prvku se zobrazí v pravém dolním rohu stavového řádku. Při výběru celé dialogové stavový řádek zobrazuje pozice dialogových oken jako celek a jeho výška a šířka.

## <a name="guides-and-grids"></a>Vodítka a mřížky

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

### <a name="to-create-edit-and-delete-guides-and-margins"></a>Pokud chcete vytvořit, upravit a odstranit vodítek a okrajů

Ať už přesouváte ovládací prvky, přidání ovládacích prvků nebo změna uspořádání aktuální rozložení, příručky pomáhají Zarovnat ovládací prvky přesně v rámci dialogového okna. Průvodce se zobrazí jako modré čáry s koncovými body v dialogovém okně zobrazí v editoru a odpovídající šipky v pravítka v horní části a sledovat levému okraji **dialogové okno** editoru.

Při vytváření dialogového okna, jsou k dispozici čtyři okraje. Okraje jsou upravené vodítka, povolí jako modré čáry s koncovými body. Zobrazte následující akce:

- Vytvořit průvodce, v rámci pravítku, vyberte po vytvoření průvodce. (Jedním kliknutím vytvoří nový průvodce; spuštění dvojitým kliknutím **nastavení vodítek** dialogovému oknu, ve kterém můžete zadat nastavení vodítek.)

- Pokud chcete nastavit vodítko, v dialogovém okně, v průvodci vyberte a přetáhněte ho na jiné místo. (Můžete zvolit také na šipku v pravítku, chcete-li přetáhněte průvodci přidružené.) Souřadnice průvodce se zobrazí ve stavovém řádku v dolní části okna a pravítka. Přesunutí ukazatele myši na šipku v pravítku, chcete-li zobrazit přesné umístění v průvodci.

- Pokud chcete přesunout okraj, přetáhněte na okraji na novou pozici. Chcete-li okraj zmizí, přesune na okraji nulové pozice. Převést zpět na okraji, umístěte ukazatel myši na okraj nulové pozice a přesuňte do umístění na okraj.

- Odstranit průvodce, přetáhněte z dialogových oken v průvodci nebo odpovídající šipku vypnout pravítko.

### <a name="to-align-controls-on-a-guide"></a>Zarovnání ovládacích prvků podle vodítka

Úchyty pro změnu velikosti ovládacích prvků Přichytit k vodítkům při přesunutí ovládacích prvků a příručky Přichytit k ovládací prvky, pokud neexistují žádná opatření dříve přichycená k průvodci. Když průvodce se přesune, ovládací prvky, které jsou přichycená k němu také přesunout. Ovládací prvky přichycená k více než jeden Průvodce se mění velikost, pokud jeden z příručky přesunuta.

Značky v pravítka, která určují mezery v průvodci a ovládací prvky jsou definovány jednotky dialogu (dlu). DLU vychází z velikosti pole písmo dialogového okna, obvykle 8 bodu MS Shell Dlg. Vodorovné DLU je průměrná délka pole písmo dialogového okna dělený čtyři. Svislé DLU je průměrná výška písmo dělený osmidílné série.

#### <a name="to-size-a-group-of-controls-with-guides"></a>Chcete-li velikost skupiny ovládacích prvků podle vodítka

1. Přichytit k vodítko straně ovládacího prvku (nebo ovládací prvky).

1. Přetáhněte vodítko na druhé straně ovládacího prvku (nebo ovládací prvky).

   V případě potřeby s více ovládacích prvků, velikost každého se přichytil k druhé průvodce.

1. Přesuňte buď Průvodce pro nastavení velikosti ovládacího prvku (nebo ovládací prvky).

#### <a name="to-change-the-intervals-of-the-tick-marks"></a>Chcete-li změnit intervalech osové značky

Z **formátu** nabídky, zvolte **nastavení vodítek**, pak v **rozteč mřížky** v dlu zadejte novou šířku a výšku.

### <a name="to-disable-guides"></a>Chcete-li zakázat vodítka

Speciální klávesy ve spojení s myši můžete zakázat přichycení efekt vodítka. Použití **Alt** klíč zakáže přichycení efekty v průvodci vybrali. Přesunutí průvodce s **Shift** klíč zabraňuje přesunutí s příručkou Přichycený ovládací prvek.

- Zakázat přichycení efekt vodítka, přetáhněte ovládací prvek při podržení **Alt** klíč.

- Pokud chcete přesunout vodítka bez přesouvání Přichycený ovládací prvky, přetáhněte v Průvodci při podržení **Shift** klíč.

- Chcete-li vypnout vodítka, z **formátu** nabídce zvolte **nastavení vodítek**. Pak v **nastavení vodítek** dialogovém okně **vodítka rozložení**vyberte **žádný**.

   > [!NOTE]
   > Můžete také dvakrát kliknout na panelu pravítko pro přístup k **nastavení vodítek** dialogové okno.

> [!TIP]
> Je zástupce vypnout vodítka na **formátu** nabídce vyberte možnost **průvodce přepínací tlačítko**.

### <a name="to-modify-the-layout-grid"></a>Chcete-li změnit rozložení mřížky

Při uvádění nebo uspořádání ovládacích prvků v dialogovém okně, můžete pro přesnější umístění rozložení mřížky. Po zapnutí mřížky "se přichytil k" tečkované čáry mřížky jakoby zmagnetizovat zobrazí ovládací prvky. Můžete zapnout a vypnout tuto funkci "přichycení k mřížce" a změnit velikost buňky mřížky rozložení.

- Mřížky rozložení zapnout nebo vypnout, z **formátu** nabídce zvolte **nastavení vodítek**, pak zaškrtněte nebo zrušte **mřížky** tlačítko.

   Můžete řídit mřížky v jednotlivých **dialogové okno** oken editoru pomocí **Přepnout mřížku** tlačítko [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

- Chcete-li změnit velikost rozložení mřížky, z **formátu** nabídky, zvolte **nastavení vodítek**, zadejte výšku a šířku v dlu buňky v mřížce. Minimální výšku nebo šířku je 4 dlu.

## <a name="select-controls"></a>Vyberte ovládací prvky

Vyberte ovládací prvky na velikost, zarovnání, přesunutí, kopírování, nebo je odstranit a dokončete operaci, kterou chcete. Ve většině případů je třeba vybrat více než jeden ovládací prvek při použití nástroje pro velikost a zarovnání na [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Při výběru ovládacího prvku, má šedé ohraničení kolem něj plný (aktivní) nebo prázdný (neaktivní) "úchyty," squares malý, který se zobrazí v ohraničení výběru. Když vyberete více ovládacích prvků, dominantního ovládacího prvku má solid úchyty a všechny ostatní vybrané ovládací prvky mají prázdný úchyty.

Při nastavování velikosti nebo zarovnání více ovládacích prvků **dialogové okno** editor používá "dominantního ovládacího prvku" zjistit, jak se ostatní ovládací prvky velikosti nebo zarovnána. Ve výchozím nastavení dominantní ovládací prvek je první ovládací prvek.

### <a name="to-select-controls"></a>Chcete-li vybrat ovládací prvky

1. V [okno nástrojů](/visualstudio/ide/reference/toolbox), vyberte **ukazatel** nástroj.

1. Svůj výběr použijte jednu z následujících kroků:

   - Tažením nakreslete rámeček výběru okolo ovládací prvky, které chcete vybrat ve vašem dialogovém okně. Když uvolníte tlačítko myši, všechny řídí uvnitř a protínající se operátory jsou vybrané pole výběru.

   - Podržte stisknutou klávesu **Shift** klíče a vyberte ovládací prvky, které chcete zahrnout do výběru.

   - Podržte stisknutou klávesu **Ctrl** klíče a vyberte ovládací prvky, které chcete zahrnout do výběru.

1. Chcete-li přidat nebo odebrat ze skupiny z vybraných ovládacích prvků ovládací prvek, podržte **Shift** klíče a vyberte ovládací prvek, který chcete přidat nebo odebrat.

> [!NOTE]
> Podržení **Ctrl** klíč a výběru ovládacího prvku Výběr způsobí, že, které řídí dominantního ovládacího prvku v tomto výběru.

### <a name="to-select-a-dominant-control"></a>Chcete-li vybrat dominantního ovládacího prvku

- Chcete-li určit, dominantní ovládací prvek, podržte **Ctrl** klíče a vyberte ovládací prvek, kterou chcete použít k ovlivnění velikosti či umístění jiných ovládacích prvků *první*.

- Chcete-li změnit dominantního ovládacího prvku, Vymazat aktuální výběr tím, že výběr mimo aktuálně vybrané ovládací prvky a opakujte předchozí postup nejprve výběr jiného ovládacího prvku.

> [!NOTE]
> Úchyty dominantního ovládacího prvku jsou pořádné popisovače podřízených ovládacích prvků, které jsou prázdné. Všechny další změny velikosti nebo zarovnání podle dominantního ovládacího prvku.

## <a name="size-controls"></a>Velikost ovládacích prvků

Použijte úchyty pro změnu velikosti ovládacího prvku. Pokud je ukazatel myši umístěn na úchyt pro změnu velikosti, změní tvar, který má označení směry, ve kterých můžete změnit velikost ovládacího prvku. Aktivní úchyty jsou pořádné a pokud úchyt pro změnu velikosti je prázdný, nelze změnit velikost ovládacího prvku podél osy.

> [!TIP]
> Můžete také změnit velikost ovládacího prvku pomocí přichycení vodítka a okraje ovládacího prvku, nebo přesunutím jeden přichycené zobrazení ovládacího prvku a Průvodce mimo jiné.

### <a name="to-size-a-control"></a>Pro nastavení velikosti ovládacího prvku

1. Vyberte ovládací prvek.

1. Přetažením úchytů změňte velikost ovládacího prvku:

   - Velikost obslužné rutiny na začátku a konce změnit velikost vodorovně nebo svisle.

   - Velikost popisovače v rozích změnit velikost vodorovné a svislé.

   > [!TIP]
   > Můžete změnit velikost jednotky jeden dialogového okna ovládacího prvku (DLU) současně současným **Shift** klíče a pomocí **vpravo** a **dolů** klávesy se šipkami.

> [!TIP]
> Chcete-li automaticky velikost ovládacího prvku podle textu v ní, otevřete **formátu** nabídky nebo klikněte pravým tlačítkem na ovládací prvek a zvolte **velikost obsahu**.

### <a name="to-make-controls-the-same-size"></a>Aby se řídí stejnou velikost

Změnit velikost skupiny ovládacích prvků na základě velikosti dominantního ovládacího prvku.

1. Vyberte ovládací prvky, které chcete změnit velikost.

   Ovládací prvek nejprve v řadě je dominantního ovládacího prvku. Konečné velikosti ovládacích prvků ve skupině závisí na velikosti dominantního ovládacího prvku.

1. Z **formátu** nabídce zvolte **nastavit stejnou velikost**, zvolte buď **obě**, **výška**, nebo **šířka**.

### <a name="combo-box"></a>Pole se seznamem

Při přidání do dialogových oken, můžete měnit velikost pole se seznamem. Můžete také určit velikost pole rozevíracího seznamu. Další informace najdete v tématu [přidání hodnot do ovládacího prvku pole se seznamem](../windows/adding-values-to-a-combo-box-control.md).

1. Vyberte tlačítko se šipkou rozevíracího seznamu na pravé straně pole se seznamem.

   ![Šipka na pole se seznamem v projektu knihovny MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Přehled ovládacího prvku změn zobrazíte velikost pole se seznamem s rozevíracího seznamu oblastí extended.

1. Chcete-li změnit počáteční velikost oblasti rozevíracího seznamu použijte dolní úchyt pro změnu velikosti.

   ![Pole se seznamem&#45;nastavení velikosti pole v projektu knihovny MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Vyberte šipku rozevíracího seznamu zavřete rozevírací část pole se seznamem.

### <a name="horizontal-scroll-bar"></a>Vodorovného posuvníku

Když přidáte seznam s vodorovný posuvník do dialogového okna pomocí tříd knihovny MFC, posuvník nezobrazí automaticky ve vaší aplikaci.

Nastavte maximální šířku prvku nejširší voláním [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) ve vašem kódu. Bez této sady hodnot posuvník nezobrazí, i když jsou položky v seznamu širší než pole.

## <a name="align-controls"></a>Zarovnání ovládacích prvků

1. Vyberte ovládací prvky, které chcete, aby bylo v souladu. Vyberte ovládací prvek, který má být dominantním nejprve nebo nastavit tak, aby se dominantního ovládacího prvku před provádění zarovnání nebo změny velikosti příkazu.

   Konečná pozice skupiny ovládacích prvků, závisí na pozici dominantního ovládacího prvku.

1. Z **formátu** nabídce zvolte **zarovnat**a pak vyberte jednu z následujících zarovnání:

   |Zarovnání|Popis|
   |-----|-----------|
   |`Lefts`|Zarovná vybrané ovládací prvky jejich levé strany.|
   |`Centers`|Zarovná vybrané ovládací prvky vodorovně jejich bodů System center.|
   |`Rights`|Zarovná vybrané ovládací prvky jejich pravé straně.|
   |`Tops`|Zarovná vybrané ovládací prvky jeho horní hrany.|
   |`Middles`|Zarovná vybraných ovládacích prvků svisle podél jejich střední body.|
   |`Bottoms`|Zarovná vybrané ovládací prvky dolního okraje.|

### <a name="to-even-spacing-between-controls"></a>Do rovnoměrných mezer mezi ovládacími prvky

**Dialogové okno** editor umožňuje ovládacích prvků místo rovnoměrně mezi nejkrajnější vybraných ovládacích prvků.

1. Vyberte ovládací prvky, které chcete změnit uspořádání.

1. Z **formátu** nabídce zvolte **místo rovnoměrně**a pak vyberte jednu z následujících zarovnání mezery:

   |Mezery|Popis|
   |---|---|
   |`Across`|Ovládací prvky místo rovnoměrně mezi první a poslední ovládací prvek.|
   |`Down`|Ovládací prvky místo rovnoměrně mezi horní a nejspodnějších ovládací prvek.|

### <a name="to-center-controls"></a>Zarovnat na střed ovládacích prvků

1. Vyberte ovládací prvek nebo prvky, které chcete změnit uspořádání.

1. Z **formátu** nabídce zvolte **Center v dialogovém okně**a pak vyberte jednu z následujících opatření:

   |Uspořádání|Popis|
   |---|---|
   |`Vertical`|Ovládací prvky v dialogovém okně svisle na střed.|
   |`Horizontal`|Ovládací prvky v dialogovém okně vodorovně na střed.|

### <a name="to-arrange-push-buttons"></a>Uspořádání tlačítek

1. Vyberte jeden nebo více tlačítek.

1. Z **formátu** nabídce zvolte **uspořádat tlačítka**a pak vyberte jednu z následujících opatření:

   |Uspořádání|Popis|
   |---|---|
   |`Right`|Zarovná tlačítek podél pravého okraje dialogového okna.|
   |`Bottom`|Zarovná tlačítek podél dolního okraje dialogového okna.|

   Pokud vyberete ovládací prvek než příkazové tlačítko, jeho pozice nemá vliv.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)