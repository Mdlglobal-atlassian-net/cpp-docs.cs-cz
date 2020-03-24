---
title: 'Postupy: ovládací prvky rozložení (C++) | Microsoft Docs'
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
ms.openlocfilehash: ee732cfb414f011e95edbbb57b218d81179d44f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168574"
---
# <a name="how-to-layout-controls-c"></a>Postupy: ovládací prvky rozložení (C++)

**Editor dialogových oken** nabízí nástroje pro rozložení, které automaticky zarovnají a mění velikost ovládacích prvků. Pro většinu úloh můžete použít [panel nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Všechny příkazy panelu nástrojů **editoru dialogového okna** jsou také k dispozici v nabídce **Formát** a většina má [klávesové zkratky](../windows/accelerator-keys-for-the-dialog-editor.md).

Mnohé příkazy rozložení pro dialogová okna jsou k dispozici pouze v případě, že je vybráno více než jeden ovládací prvek. Můžete vybrat jeden ovládací prvek nebo více ovládacích prvků a pokud je vybráno více než jeden ovládací prvek, tak první, který vyberete, je ve výchozím nastavení dominantní ovládací prvek.

Umístění, Výška a šířka aktuálního ovládacího prvku se zobrazí v pravém dolním rohu stavového řádku. Po výběru celého dialogového okna se ve stavovém řádku zobrazí pozice dialogového okna jako celku a jeho výška a šířka.

## <a name="arrange-controls"></a>Uspořádat ovládací prvky

Ovládací prvky můžete uspořádat na dialogová okna pomocí **editoru dialogových** oken v jednom ze tří různých stavů:

- S vodítky a okraji, nastavte jako výchozí.

- S mřížkou rozložení zapnuto.

- Bez jakýchkoli funkcí Přichycení nebo zarovnání.

[Panel nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) obsahuje tlačítka, která ovládají stav.

- Chcete-li změnit stav, vyberte příslušnou ikonu nebo přejděte do nabídky **formát** > **nastavení Průvodce**.

Dialogové okno **nastavení Průvodce** má následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Vodítka rozložení**|Zobrazí nastavení pro vodítka rozložení.|
|**NTato**|Skryje nástroje pro rozložení.|
|**Pravítka a vodítka**|Když je tato možnost povolená, přidá pravítka k nástrojům rozložení a umožní umístit vodítka do pravítek. Výchozími vodítky jsou okraje.|
|**Mřížka**|Vytvoří mřížku rozložení. Nové ovládací prvky budou automaticky zarovnány k mřížce.|
|**Mezery mezi mřížkami**|Zobrazí nastavení pro mezery v mřížce v jednotkách dialogového okna (DLU).|
|**Šířka: dlu**|Nastaví šířku mřížky rozložení v dlu. Horizontální DLU je průměrná šířka písma dialogového okna děleného 4.|
|**Výška: dlu**|Nastaví výšku mřížky rozložení v dlu. Svislá DLU je průměrná výška písma dialogového okna děleného 8.|

### <a name="guides-and-margins"></a>Vodítka a okraje

Bez ohledu na to, zda přesouváte ovládací prvky, přidáte ovládací prvky nebo změníte uspořádání aktuálního rozložení, vodítek a okraje vám může pomáhat Zarovnat ovládací prvky přesně v rámci dialogového okna.

Při vytváření dialogového okna se k dispozici čtyři upravené příručky nazývané okraje a zobrazují se jako modré tečkované čáry.

- Chcete-li přesunout okraje, přetáhněte okraj na novou pozici.

- Chcete-li, aby okraj zmizel, přesuňte okraj na nulovou pozici.

- Chcete-li posunout okraj, umístěte ukazatel na pozici nulového okraje a přesuňte okraj na pozici.

Vodítka se zobrazí jako modré tečkované čáry v dialogovém okně zobrazeném v editoru a odpovídající šipky v horní části a na levé straně **editoru dialogového okna**. Úchyty pro změnu velikosti ovládacích prvků přichyceny k vodítkům při přesunu ovládacích prvků a ovládací prvky přichyceny k ovládacím prvkům, pokud k vodítku nebyly dříve přichyceny žádné ovládací prvky. Při přesunutí vodítka jsou také přesunuty ovládací prvky, které jsou přichyceny. Ovládací prvky přichycené k více než jednomu vodítku se mění při přesunu jednoho z vodítek.

- Pokud chcete vytvořit vodítko v rámci pravítka, vyberte jednu z nich, abyste vytvořili vodítko, nebo poklikejte na dialogové okno **nastavení Průvodce** , kde můžete zadat nastavení příručky.

- Chcete-li nastavit vodítko v dialogovém okně, vyberte vodítko a přetáhněte ho na novou pozici nebo vyberte šipku v pravítku a přetáhněte tak přidruženou vodítko.

   Souřadnice příručky se zobrazí ve stavovém řádku v dolní části okna a v pravítku nebo přesunutím ukazatele myši na šipku v pravítku, aby se zobrazila přesná pozice průvodce.

- Chcete-li odstranit vodítko, přetáhněte vodítko z dialogového okna nebo přetáhněte odpovídající šipku mimo pravítko.

Značky v pravítku, které určují mezery mezi vodítky a ovládacími prvky, jsou definovány jednotkami dialogových oken (DLU). DLU je založen na velikosti dialogového okna písma, normálně v programu MS Shell s 8 body. Horizontální DLU je průměrná šířka písma dialogového okna děleného čtyřmi. Svislá DLU je průměrná výška písma děleného 8.

- Chcete-li změnit intervaly značek, přejděte na **Formát** nabídky > **Nastavení příručky**a potom v poli **rozteč mřížky** zadejte novou šířku a výšku v dlu.

### <a name="layout-grid"></a>Mřížka rozložení

Když umísťujete nebo uspořádáváte ovládací prvky v dialogovém okně, použijte mřížku rozložení pro přesnější umístění. Když je mřížka zapnutá, ovládací prvky se přichyceny k tečkovaným čarám mřížky, jako kdyby byly magnetické.

- Chcete-li zapnout nebo vypnout mřížku rozložení, přejděte do nabídky **formát** > **nastavení Průvodce** a vyberte nebo zrušte zaškrtnutí tlačítka **Mřížka** .

   Mřížku v jednotlivých oknech **Editor dialogových** oken můžete i nadále ovládat pomocí tlačítka **Přepnout mřížku** na [panelu nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

- Chcete-li změnit velikost mřížky rozložení, přejděte do nabídky **formát** > **nastavení Průvodce** a zadejte výšku a šířku v dlu pro buňky v mřížce. Minimální výška nebo šířka je 4.

### <a name="disable-guides"></a>Zakázat vodítka

Pomocí speciálních kláves můžete v kombinaci s myší zakázat efekt přichycení vodítek. Použití klávesy **ALT** vypne efekty přichycení vybrané příručky. Přesunutím vodítka pomocí klávesy **SHIFT** zabráníte v přesunutí přichycených ovládacích prvků s průvodcem.

- Chcete-li vypnout efekt přichycení vodítek, přetáhněte ovládací prvek a podržte stisknutou klávesu **ALT** .

- Chcete-li přesunout vodítka bez přesunutí přichyceného ovládacího prvku, přetáhněte vodítko a podržte klávesu **SHIFT** .

- Pokud chcete vodítka vypnout, přejděte do nabídky **formát** > **nastavení Průvodce**. Pak v části **Vodítka rozložení**vyberte **žádné**.

   > [!TIP]
   > Zástupce můžete také použít ve **formátu** nabídky > **přepínání vodítek**.

## <a name="select-controls"></a>Vybrat ovládací prvky

Vyberte ovládací prvky pro velikost, zarovnání, přesunutí, zkopírování nebo odstranění a pak dokončete požadovanou operaci. Ve většině případů je třeba vybrat více než jeden ovládací prvek pro použití nástrojů pro změnu velikosti a zarovnání na [panelu nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Když je vybrán ovládací prvek, má kolem něj šedé ohraničení s plnými (aktivními) nebo prázdnými (neaktivními) úchyty, malými čtverci, které se zobrazí v ohraničení výběru. Je-li vybráno více ovládacích prvků, má dominantní ovládací prvek úchyty plné velikosti a všechny ostatní vybrané ovládací prvky mají prázdné úchyty pro změnu velikosti.

- Chcete-li vybrat ovládací prvky, v [okně Sada nástrojů](/visualstudio/ide/reference/toolbox)vyberte nástroj **ukazatel** a pomocí některého z následujících kroků proveďte výběr:

  - Přetažením ukazatele myši nakreslete pole výběru kolem ovládacích prvků, které chcete vybrat v dialogovém okně. Po uvolnění tlačítka myši jsou vybrány všechny ovládací prvky uvnitř a protínají se pole výběr.

  - Podržte stisknutou klávesu **SHIFT** a vyberte ovládací prvky, které chcete zahrnout do výběru.

  - Podržte stisknutou klávesu **CTRL** a vyberte ovládací prvky, které chcete zahrnout do výběru.

- Chcete-li přidat nebo odebrat ovládací prvek ze skupiny vybraných ovládacích prvků, podržte klávesu **SHIFT** a vyberte ovládací prvek, který chcete přidat nebo odebrat.

### <a name="dominant-controls"></a>Dominantní ovládací prvky

Při změně velikosti nebo zarovnání více ovládacích prvků **Editor dialogového okna** používá dominantní ovládací prvek k určení toho, jak mají ostatní ovládací prvky velikost nebo zarovnání. Ve výchozím nastavení je dominantní ovládací prvek prvním vybraným ovládacím prvkem.

- Chcete-li určit dominantní ovládací prvek, podržte stisknutou klávesu **CTRL** a vyberte ovládací prvek, který chcete použít k ovlivnění velikosti nebo umístění jiných ovládacích prvků jako *první*. Podržte stisknutou **klávesu CTRL** a výběr ovládacího prvku v rámci výběru, tím se ovládací prvek v tomto výběru nastaví jako dominantní.

- Chcete-li změnit dominantní ovládací prvek, vymažte aktuální výběr výběrem mimo všechny aktuálně vybrané ovládací prvky a Zopakováním výše uvedeného postupu vyberte jiný ovládací prvek jako *první*.

> [!NOTE]
> Obslužné rutiny pro změnu velikosti dominantního ovládacího prvku jsou plné, zatímco jsou ovládací prvky podřízených ovládacích prvků prázdné. Veškerá další změna velikosti nebo zarovnání je založena na dominantním ovládacím prvku.

## <a name="size-controls"></a>Ovládací prvky velikosti

Pro změnu velikosti ovládacího prvku použijte úchyty pro změnu velikosti. Když je ukazatel umístěn v úchytu pro změnu velikosti, změní obrazec na označení směrů, ve kterých lze změnit velikost ovládacího prvku. Aktivní úchyty pro změnu velikosti jsou plné, a pokud je úchyt pro změnu velikosti prázdný, nemůže být velikost ovládacího prvku podél osy změněna.

- Chcete-li nastavit velikost ovládacího prvku, vyberte ovládací prvek a přetáhněte úchyty pro změnu velikosti.

  - Úchyty velikosti v horní části a na stranách mění vodorovnou nebo svislou velikost.

  - Obslužné rutiny velikosti v rozích mění vodorovnou i svislou velikost.

   > [!TIP]
   > Můžete změnit velikost ovládacího prvku DLU (Control Unit) na jednu jednotku současně tak, že podržíte klávesu **SHIFT** a použijete klávesy šipka **vpravo** a **dolů** .

- Chcete-li automaticky nastavit velikost ovládacího prvku tak, aby odpovídal textu, přejděte do nabídky **Formát** nebo klikněte pravým tlačítkem myši na ovládací prvek a vyberte možnost **Velikost obsahu**.

- Chcete-li nastavit stejnou velikost ovládacích prvků, vyberte ovládací prvky, jejichž velikost chcete změnit, a přejděte na **Formát** nabídky > **nastavit stejnou velikost**a pak zvolte buď **obojí**, **Výška**nebo **Šířka**.

   Změníte velikost skupiny ovládacích prvků podle velikosti dominantního ovládacího prvku, který je vybraný jako první v řadě. Konečná velikost ovládacích prvků ve skupině závisí na velikosti dominantního ovládacího prvku.

- Chcete-li nastavit velikost skupiny ovládacích prvků pomocí vodítek, přichycení jedné strany ovládacího prvku (nebo ovládacích prvků) k vodítku, poté přetáhněte vodítko na druhou stranu ovládacího prvku (nebo ovládacích prvků). Nyní můžete přesunout buď vodítko pro velikost ovládacího prvku (nebo ovládacích prvků).

   V případě potřeby s více ovládacími prvky velikost každého přichycení k druhé příručce.

### <a name="other-controls"></a>Další ovládací prvky

Po přidání pole se seznamem do dialogového okna můžete změnit jeho velikost. Můžete také zadat velikost rozevíracího seznamu. Další informace najdete v tématu [Přidání hodnot do ovládacího prvku pole se seznamem](../windows/adding-values-to-a-combo-box-control.md).

1. Vyberte tlačítko se šipkou rozevíracího seznamu na pravé straně pole se seznamem.

   ![Šipka na poli se seznamem v projektu knihovny MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Obrys ovládacího prvku se změní, aby se zobrazila velikost pole se seznamem se rozšířenou oblastí rozevíracího seznamu.

1. Chcete-li změnit počáteční velikost oblasti rozevíracího seznamu, použijte úchyt pro snížení velikosti.

   ![Přizpůsobení&#45;velikosti pole se seznamem v projektu knihovny MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Opětovným výběrem šipky rozevíracího seznamu zavřete část rozevíracího seznamu pole se seznamem.

> [!NOTE]
> Když přidáte seznam se seznamem s vodorovným posuvníkem do dialogového okna pomocí knihovny MFC, posuvník se v aplikaci automaticky nezobrazí.
>
> Nastavte maximální šířku pro nejširší prvek voláním [CListBox –:: SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) ve vašem kódu. Bez této hodnoty se posuvník nezobrazí, ani když jsou položky v poli seznam širší, než pole.

## <a name="align-controls"></a>Zarovnat ovládací prvky

- Chcete-li zarovnat ovládací prvky, vyberte ovládací prvky, které chcete zarovnat. Přejděte na **Formát** nabídky > **zarovnejte** a vyberte jedno z následujících zarovnání:

   |Zarovnání|Popis|
   |-----|-----------|
   |**Doleva**|Zarovnává vybrané ovládací prvky podél jejich levé strany.|
   |**Psaní**|Zarovnává vybrané ovládací prvky vodorovně podél jejich středových bodů.|
   |**Rights**|Zarovná vybrané ovládací prvky podél pravé strany.|
   |**Zbarvení**|Zarovná vybrané ovládací prvky podél horních hran.|
   |**Svisle na střed**|Zarovnává vybrané ovládací prvky svisle podél jejich středních bodů.|
   |**Dolů**|Zarovná vybrané ovládací prvky podél dolních hran.|

   Nezapomeňte vybrat ovládací prvek, který má být dominantní jako první, nebo před provedením příkazu Zarovnat nebo změnit velikost nastavit, aby byl dominantní ovládací prvek, protože poslední pozice skupiny ovládacích prvků závisí na poloze dominantního ovládacího prvku.

- Do rovnoměrného prostoru ovládací prvky vyberte ovládací prvky, jejichž uspořádání chcete změnit. Přejděte do nabídky **formát** > **prostor rovnoměrně** a vyberte jedno z následujících zarovnání mezer:

   |Mezery|Popis|
   |---|---|
   |**Čtečce**|Rovnoměrné ovládací prvky prostoru mezi nejvíce vlevo a vybraným ovládacím prvkem vpravo.|
   |**Dolů**|Rovnoměrné ovládací prvky prostoru mezi horním a spodním ovládacím prvkem.|

- Chcete-li vycentrovat ovládací prvky, vyberte ovládací prvek nebo ovládací prvky, které chcete změnit. **V dialogovém okně** přejděte na **Formát** nabídky > Center a vyberte jedno z následujících uspořádání:

   |Úprava|Popis|
   |---|---|
   |**Svislé**|Vycentrovat ovládací prvky v dialogovém okně svisle.|
   |**Horizontální**|Vycentrovat ovládací prvky vodorovně v dialogovém okně.|

- Chcete-li zarovnat tlačítka nabízených oznámení, vyberte jedno nebo více nabízených tlačítek. Přejděte do nabídky **formát** > **Uspořádat tlačítka**a pak zvolte jedno z následujících uspořádání:

   |Úprava|Popis|
   |---|---|
   |**Kliknutím**|Zarovnává tlačítka pro vložení podél pravého okraje dialogového okna.|
   |**Dolů**|Zarovná tlačítka nahoru podél dolního okraje dialogového okna.|

   Pokud vyberete jiný ovládací prvek než nabízené tlačítko, jeho pozice to neovlivní.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Spravovat ovládací prvky dialogového okna](controls-in-dialog-boxes.md)<br/>
[Postupy: Přidání, úprava nebo odstranění ovládacích prvků](adding-editing-or-deleting-controls.md)<br/>
[Postupy: definování přístupu a hodnot řízení](defining-mnemonics-access-keys.md)<br/>
