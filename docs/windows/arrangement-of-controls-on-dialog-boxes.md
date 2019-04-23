---
title: 'Postupy: Rozložení ovládacích prvků (C++) | Dokumentace Microsoftu'
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
ms.openlocfilehash: 878b7371dfa77880d68f1001444ed44b84d7240c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037418"
---
# <a name="how-to-layout-controls-c"></a>Postupy: Rozložení ovládacích prvků (C++)

**Editoru dialogového okna** poskytuje rozložení nástroje, které Zarovnat a nastavení velikosti ovládacích prvků automaticky. Pro většinu úloh můžete použít [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Všechny **editoru dialogového okna** nástrojů příkazy jsou také k dispozici na **formátu** nabídky a většina mají [klávesových zkratek](../windows/accelerator-keys-for-the-dialog-editor.md).

Mnoho příkazů rozložení pro dialogová okna jsou k dispozici, jenom když vyberete více než jeden ovládací prvek. Můžete vybrat ovládací prvek jednoho nebo více ovládacích prvků a při výběru více než jeden ovládací prvek první z nich, kterou vyberete je ve výchozím nastavení dominantního ovládacího prvku.

Umístění, výšku a šířku aktuálního ovládacího prvku se zobrazí v pravém dolním rohu stavového řádku. Při výběru celé dialogové stavový řádek zobrazuje pozice dialogových oken jako celek a jeho výška a šířka.

## <a name="arrange-controls"></a>Uspořádání ovládacích prvků

Můžete uspořádat ovládací prvky v dialogových oknech s **editoru dialogového okna** v jednom ze tří různých stavů:

- Pomocí vodítek a okrajů na nastavte jako výchozí.

- Pomocí mřížky rozložení v.

- Bez snap nebo zarovnání funkcí.

[Nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) obsahuje tlačítka, která řídí stav.

- Chcete-li změnit stav, vyberte příslušnou položku nebo přejděte do nabídky **formátu** > **nastavení vodítek**.

**Nastavení vodítek** dialogové okno má následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Vodítka rozložení**|Zobrazuje nastavení vodítek rozložení.|
|**Žádné**|Skryje nástroje rozložení.|
|**Pravítka a vodítka**|Pokud povolená, přidá do nástroje pro rozložení pravítka a umožňuje umístit do pravítek, kteří. Výchozí příručky jsou okraje.|
|**Mřížka**|Vytvoří rozložení mřížky. Nové ovládací prvky budou automaticky zarovnat k mřížce.|
|**Rozteč mřížky**|Nastavení pro rozteč mřížky se zobrazí v poli jednotky dialogu (dlu).|
|**Width: Dlu**|Nastavuje šířku mřížky rozložení v dlu. Vodorovné DLU je průměrná délka pole písmo dialogového okna dělený 4.|
|**Height: Dlu**|Nastaví výšku mřížky rozložení v dlu. Svislé DLU je průměrná výška pole písmo dialogového okna dělený 8.|

### <a name="guides-and-margins"></a>Vodítek a okrajů

Ať už přesouváte ovládací prvky, přidání ovládacích prvků nebo změny uspořádání aktuální rozložení, vodítek a okrajů může pomoct Zarovnat ovládací prvky přesně v rámci dialogového okna.

Při vytváření dialogového okna čtyři upravené vodítka volá okraje jsou k dispozici a zobrazí jako modré čáry s koncovými body.

- Pokud chcete přesunout okraj, přetáhněte na okraji na novou pozici.

- Chcete-li okraj zmizí, přesune na okraji nulové pozice.

- Převést zpět na okraji, umístěte ukazatel myši na okraj nulové pozice a přesuňte do umístění na okraj.

Průvodce se zobrazí jako modré čáry s koncovými body v dialogovém okně zobrazí v editoru a odpovídající šipky v pravítka v horní části a sledovat levému okraji **editoru dialogového okna**. Úchyty pro změnu velikosti ovládacích prvků Přichytit k vodítkům při přesunutí ovládacích prvků a příručky Přichytit k ovládací prvky, pokud neexistují žádná opatření dříve přichycená k průvodci. Když průvodce se přesune, ovládací prvky, které jsou přichycená k němu také přesunout. Ovládací prvky přichycená k více než jeden Průvodce se mění velikost, pokud jeden z příručky přesunuta.

- Vytvořit průvodce v rámci pravítku, vyberte po vytvoření průvodce nebo dvakrát klikněte na Spustit **nastavení vodítek** dialogovému oknu, kde můžete určit nastavení průvodce.

- V dialogovém okně Nastavit vodítko, vyberte v průvodci a přetáhněte ji na jiné místo nebo vyberte šipku v pravítku, chcete-li přetáhněte přidružené průvodce.

   Souřadnice průvodce se zobrazí ve stavovém řádku v dolní části okna a pravítka nebo přesunutí ukazatele myši na šipku v pravítku, chcete-li zobrazit přesné umístění v průvodci.

- Odstranit průvodce, přetáhněte z dialogových oken v průvodci nebo odpovídající šipku vypnout pravítko.

Značky v pravítka, která určují mezery v průvodci a ovládací prvky jsou definovány jednotky dialogu (dlu). DLU vychází z velikosti pole písmo dialogového okna, obvykle 8 bodu MS Shell Dlg. Vodorovné DLU je průměrná délka pole písmo dialogového okna dělený čtyři. Svislé DLU je průměrná výška písmo dělený 8.

- Chcete-li změnit intervalech značek, přejděte do nabídky **formátu** > **nastavení vodítek**, pak v **rozteč mřížky** zadejte novou šířku a výšku v dlu.

### <a name="layout-grid"></a>Rozložení mřížky

Když při umísťování nebo uspořádání ovládacích prvků v dialogovém okně, použijte mřížky rozložení pro přesnější umístění. Po zapnutí mřížky budou ovládací prvky přichytí k tečkované čáry mřížky, jako kdyby zmagnetizovat.

- Rozložení mřížky zapnout nebo vypnout, přejděte do nabídky **formátu** > **nastavení vodítek** a zaškrtněte nebo zrušte zaškrtnutí **mřížky** tlačítko.

   Můžete řídit mřížky v jednotlivých **editoru dialogového okna** windows s využitím **Přepnout mřížku** tlačítko [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

- Chcete-li změnit velikost rozložení mřížky, přejděte do nabídky **formátu** > **nastavení vodítek** a napište výšku a šířku v dlu buňky v mřížce. Minimální výšku nebo šířku je 4.

### <a name="disable-guides"></a>Zakázání vodítek

Speciální klávesy ve spojení s myši můžete zakázat přichycení efekt vodítka. Použití **Alt** klíč zakáže přichycení efekty v průvodci vybrali. Přesunutí průvodce s **Shift** klíč zabraňuje přesunutí s příručkou Přichycený ovládací prvek.

- Zakázat přichycení efekt vodítka, přetáhněte ovládací prvek při podržení **Alt** klíč.

- Pokud chcete přesunout vodítka bez přesouvání Přichycený ovládací prvky, přetáhněte v Průvodci při podržení **Shift** klíč.

- Chcete-li vypnout vodítka, přejděte do nabídky **formátu** > **nastavení vodítek**. Potom v části **vodítka rozložení**vyberte **žádný**.

   > [!TIP]
   > Můžete také použít zástupce v nabídce **formátu** > **průvodce přepínací tlačítko**.

## <a name="select-controls"></a>Vyberte ovládací prvky

Vyberte ovládací prvky na velikost, zarovnání, přesunutí, kopírování, nebo je odstranit a dokončete operaci, kterou chcete. Ve většině případů je třeba vybrat více než jeden ovládací prvek při použití nástroje pro velikost a zarovnání na [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Při výběru ovládacího prvku má šedé ohraničení s ucelený (aktivní) nebo prázdný (neaktivní) úchyty, malých čtverečků, které se zobrazují v ohraničení výběru. Když vyberete více ovládacích prvků, dominantního ovládacího prvku má solid úchyty a všechny ostatní vybrané ovládací prvky mají prázdný úchyty.

- Vyberte ovládací prvky, v [okno nástrojů](/visualstudio/ide/reference/toolbox), vyberte **ukazatel** nástroje a použijte jednu z následujících kroků svůj výběr:

  - Tažením nakreslete rámeček výběru okolo ovládací prvky, které chcete vybrat ve vašem dialogovém okně. Když uvolníte tlačítko myši, všechny řídí uvnitř a protínající se operátory jsou vybrané pole výběru.

  - Podržte stisknutou klávesu **Shift** klíče a vyberte ovládací prvky, které chcete zahrnout do výběru.

  - Podržte stisknutou klávesu **Ctrl** klíče a vyberte ovládací prvky, které chcete zahrnout do výběru.

- Chcete-li přidat nebo odebrat ze skupiny z vybraných ovládacích prvků ovládací prvek, podržte **Shift** klíče a vyberte ovládací prvek, který chcete přidat nebo odebrat.

### <a name="dominant-controls"></a>Dominantní ovládací prvky

Při nastavování velikosti nebo zarovnání více ovládacích prvků **editoru dialogového okna** používá dominantního ovládacího prvku k určení, jak se ostatní ovládací prvky velikosti nebo zarovnána. Ve výchozím nastavení dominantní ovládací prvek je první ovládací prvek.

- Chcete-li určit, dominantní ovládací prvek, podržte **Ctrl** klíče a vyberte ovládací prvek, kterou chcete použít k ovlivnění velikosti či umístění jiných ovládacích prvků *první*. Podržení **Ctrl** klíč a výběru ovládacího prvku Výběr také zjednoduší, které řídí dominantního ovládacího prvku v tomto výběru.

- Chcete-li změnit dominantního ovládacího prvku, Vymazat aktuální výběr tím, že výběr mimo aktuálně vybrané ovládací prvky a opakujte výše uvedeného postupu, že vyberete jiný ovládací prvek *první*.

> [!NOTE]
> Úchyty dominantního ovládacího prvku jsou pořádné popisovače podřízených ovládacích prvků, které jsou prázdné. Všechny další změny velikosti nebo zarovnání podle dominantního ovládacího prvku.

## <a name="size-controls"></a>Velikost ovládacích prvků

Použijte úchyty pro změnu velikosti ovládacího prvku. Pokud je ukazatel myši umístěn na úchyt pro změnu velikosti, změní tvar, který má označení směry, ve kterých můžete změnit velikost ovládacího prvku. Aktivní úchyty jsou pořádné a pokud úchyt pro změnu velikosti je prázdný, nelze změnit velikost ovládacího prvku podél osy.

- Velikost ovládacího prvku, vyberte ovládací prvek a přetažením úchytů změňte velikost.

  - Velikost obslužné rutiny na začátku a konce změnit velikost vodorovně nebo svisle.

  - Velikost popisovače v rozích změnit velikost vodorovné a svislé.

   > [!TIP]
   > Můžete změnit velikost jednotky jeden dialogového okna ovládacího prvku (DLU) současně současným **Shift** klíče a pomocí **vpravo** a **dolů** klávesy se šipkami.

- Automaticky upravit velikost ovládacího prvku podle textu v ní, přejděte do nabídky **formátu** nebo klikněte pravým tlačítkem na ovládací prvek a zvolte **velikost obsahu**.

- Chcete-li ovládacích prvků se stejnou velikostí, vyberte ovládací prvky, které chcete změnit velikost a přejděte do nabídky **formátu** > **nastavit stejnou velikost**, zvolte buď **obě**, **Výška**, nebo **šířka**.

   Můžete změnit velikost skupiny ovládacích prvků na základě velikosti dominantního ovládacího prvku, který je ovládací prvek nejprve v řadě. Konečné velikosti ovládacích prvků ve skupině závisí na velikosti dominantního ovládacího prvku.

- Velikost skupiny ovládacích prvků podle vodítka, Přichytit k vodítko straně ovládacího prvku (nebo ovládací prvky) a potom přetáhněte vodítko na druhé straně ovládacího prvku (nebo ovládací prvky). Nyní můžete přesunout buď Průvodce pro nastavení velikosti ovládacího prvku (nebo ovládací prvky).

   V případě potřeby s více ovládacích prvků, velikost každého se přichytil k druhé průvodce.

### <a name="other-controls"></a>Další ovládací prvky

Při přidání do dialogových oken, můžete měnit velikost pole se seznamem. Můžete také určit velikost pole rozevíracího seznamu. Další informace najdete v tématu [přidání hodnot do ovládacího prvku pole se seznamem](../windows/adding-values-to-a-combo-box-control.md).

1. Vyberte tlačítko se šipkou rozevíracího seznamu na pravé straně pole se seznamem.

   ![Šipka na pole se seznamem v projektu knihovny MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Přehled ovládacího prvku změn zobrazíte velikost pole se seznamem s rozevíracího seznamu oblastí extended.

1. Chcete-li změnit počáteční velikost oblasti rozevíracího seznamu použijte dolní úchyt pro změnu velikosti.

   ![Pole se seznamem&#45;nastavení velikosti pole v projektu knihovny MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Vyberte šipku rozevíracího seznamu zavřete rozevírací část pole se seznamem.

> [!NOTE]
> Když přidáte seznam s vodorovný posuvník do dialogového okna pomocí knihovny MFC, posuvník se nezobrazí automaticky ve vaší aplikaci.
>
> Nastavte maximální šířku prvku nejširší voláním [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) ve vašem kódu. Bez této sady hodnot posuvník nezobrazí, i když jsou položky v seznamu širší než pole.

## <a name="align-controls"></a>Zarovnání ovládacích prvků

- Chcete-li zarovnat ovládací prvky, vyberte ovládací prvky, které chcete, aby bylo v souladu. Přejděte do nabídky **formátu** > **zarovnat** a zvolte jednu z následujících zarovnání:

   |Zarovnání|Popis|
   |-----|-----------|
   |**Eva**|Zarovná vybrané ovládací prvky jejich levé strany.|
   |**Centra**|Zarovná vybrané ovládací prvky vodorovně jejich bodů System center.|
   |**Práva**|Zarovná vybrané ovládací prvky jejich pravé straně.|
   |**Lineárních**|Zarovná vybrané ovládací prvky jeho horní hrany.|
   |**Středy**|Zarovná vybraných ovládacích prvků svisle podél jejich střední body.|
   |**DNA**|Zarovná vybrané ovládací prvky dolního okraje.|

   Vyberte ovládací prvek, který má být dominantním nejprve nebo nastavit tak, aby se dominantního ovládacího prvku před provádění zarovnání nebo změny velikosti příkaz, protože konečné umístění skupiny ovládacích prvků, závisí na pozici dominantního ovládacího prvku.

- Pokud chcete rovnoměrně rozmístění ovládacích prvků vyberte ovládací prvky, které chcete změnit uspořádání. Přejděte do nabídky **formátu** > **místo rovnoměrně** a zvolte jednu z následujících zarovnání mezery:

   |Mezery|Popis|
   |---|---|
   |**Mezi**|Ovládací prvky místo rovnoměrně mezi první a poslední ovládací prvek.|
   |**Down**|Ovládací prvky místo rovnoměrně mezi horní a nejspodnějších ovládací prvek.|

- Zarovnat na střed ovládací prvky, vyberete ovládací prvek nebo prvky, které chcete změnit uspořádání. Přejděte do nabídky **formátu** > **Center v dialogovém okně** a zvolte jednu z následujících opatření:

   |Uspořádání|Popis|
   |---|---|
   |**Svisle**|Ovládací prvky v dialogovém okně svisle na střed.|
   |**Vodorovná**|Ovládací prvky v dialogovém okně vodorovně na střed.|

- Chcete-li zarovnat tlačítek, vyberte jeden nebo více tlačítek. Přejděte do nabídky **formátu** > **uspořádat tlačítka**, pak vyberte jednu z následujících opatření:

   |Uspořádání|Popis|
   |---|---|
   |**doprava**|Zarovná tlačítek podél pravého okraje dialogového okna.|
   |**dolní**|Zarovná tlačítek podél dolního okraje dialogového okna.|

   Pokud vyberete ovládací prvek než příkazové tlačítko, jeho pozice nemá vliv.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Správa ovládací prvky dialogového okna](controls-in-dialog-boxes.md)<br/>
[Postupy: Přidání, úprava nebo odstranění ovládacích prvků](adding-editing-or-deleting-controls.md)<br/>
[Postupy: Definování řízení přístupu a hodnot](defining-mnemonics-access-keys.md)<br/>