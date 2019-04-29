---
title: Editor dialogových oken (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
- vc.editors.dialog
helpviewer_keywords:
- resource editors [C++], Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes [C++], editing
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog Editor [C++], showing or hiding toolbar
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog Editor [C++], accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog Editor [C++], switching between controls and code
- Dialog Editor [C++], shortcut keys
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
ms.openlocfilehash: dc5a823951e07af96efceec52d2aa23552c2d002
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414259"
---
# <a name="dialog-editor-c"></a>Editor dialogových oken (C++)

**Editoru dialogového okna** umožňuje vytvoření nebo úpravu prostředků dialogových oken.

- Chcete-li otevřít editor, dvakrát klikněte na soubor .rc dialogu v **zobrazení prostředků** okno a přejděte do nabídky **zobrazení** > **zobrazení prostředků**.

Jeden z prvních kroků při vytváření nové dialogové okno nebo šablony dialogového okna, je přidání ovládacích prvků. V **editoru dialogového okna**, můžete uspořádat ovládací prvky podle určité velikosti, tvaru nebo zarovnání, nebo je můžete přesouvat přibližně pro práci v dialogovém okně. Rovněž lze ovládací prvky snadno odstranit.

Dialogové okno lze uložit jako šablonu, takže je možné jej znovu použít. Rovněž lze snadno přepínat mezi návrhem dialogového okna a editací kódu, který jej implementuje.

Je také možné upravovat vlastnosti jednoho nebo více ovládacích prvků v **editoru dialogového okna**. Můžete změnit pořadí ovládacích prvků, to znamená, když pořadí, ve kterém ovládací prvky získávají zaměřit **kartu** stisknutí klávesy, nebo můžete definovat přístupové klávesy nebo kombinace kláves, která umožňuje uživatelům vybrat ovládací prvek pomocí klávesnice.

**Editoru dialogového okna** také umožňuje použití vlastních ovládacích prvků, včetně ovládacích prvků ActiveX. Můžete také upravit [zobrazení formuláře](../mfc/reference/cformview-class.md), [zaznamenat zobrazení](../data/record-views-mfc-data-access.md), nebo [dialogové pruhy](../mfc/dialog-bars.md).

Od verze Visual Studio 2015, můžete použít **editoru dialogového okna** k definování dynamického rozložení, které určují, jak přesunout ovládacích prvků a změna velikosti, když uživatel změní dialogové okno. Další informace najdete v tématu [dynamické rozložení](../mfc/dynamic-layout.md).

Další informace o prostředcích naleznete v tématu Jak [vytvoření dialogového okna](../windows/creating-a-new-dialog-box.md) a [ovládací prvky dialogového okna](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Při použití **editoru dialogového okna**, v mnoha případech můžete vybrat pomocí pravé tlačítko myši zobrazit místní nabídku s často používanými příkazy.

## <a name="dialog-editor-toolbar"></a>Panel nástrojů editoru dialogového okna

**Editoru dialogového okna** nástrojů obsahuje tlačítka pro uspořádání rozložení ovládacích prvků v dialogovém okně třeba velikost a zarovnání. **Editor dialogových oken** tlačítka na panelu nástrojů odpovídají příkazy na **formátu** nabídky.

|Ikona|Význam|Ikona|Význam|
|----------|-------------|----------|-------------|
|![Tlačítko Testovat Dialog](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Testovací dialogové okno|![Místo přes tlačítko](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Mezi|
|![Zarovnat doleva tlačítko](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Zarovnat doleva|![Tlačítko místo dolů](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Dolů|
|![Zarovnat práva tlačítko](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Zarovnat doprava|![Ujistěte se stejnou šířku tlačítka](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Nastavit stejnou šířku|
|![Zarovnat horní tlačítko](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Zarovnat nahoru|![Ujistěte se stejnou výškou tlačítko](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Stejná výška|
|![Zarovnat DNA tlačítko](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Zarovnat dolů|![Ujistěte se stejnou velikostí tlačítko](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Nastavit stejnou velikost|
|![Tlačítko svisle Center](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Svisle|![Přepínací tlačítko mřížky](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Přepnout mřížku|
|![Vodorovná tlačítka Center](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Vodorovná|![Tlačítko průvodce přepínací tlačítko](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Průvodce přepínací tlačítko|

- Zobrazení nebo skrytí **editoru dialogového okna** nástrojů, přejděte do nabídky **zobrazení** > **panely nástrojů** > **editoru dialogového okna**.

Když otevřete **editoru dialogového okna** v projektu v jazyce C++ **editoru dialogového okna** nástrojů se automaticky zobrazí v horní části vašeho řešení, ale pokud explicitně Zavřít panel nástrojů, bude nutné ho vyvolat Při příštím otevření **editoru dialogového okna**. Zobrazení můžete přepínat výběrem ze seznamu dostupných panelů nástrojů a oken.

## <a name="switch-between-dialog-box-controls-and-code"></a>Přepínání mezi ovládacími prvky dialogového okna a kódem

V aplikacích MFC můžete dvakrát kliknout na dialogové okno Ovládací prvky pro přechod na svůj kód obslužné rutiny nebo k rychlému vytvoření zástupné procedury funkcí obslužných rutin.

Ovládací prvek, vyberte **ControlEvents** tlačítko nebo **zprávy** tlačítko [okno vlastností](/visualstudio/ide/reference/properties-window) Chcete-li zobrazit úplný seznam událostí a zpráv Windows k dispozici pro vybranou položku. Zvolte ze seznamu a vytvořit nebo upravit funkce obslužné rutiny.

- Pro přechod na kód z **editoru dialogového okna**, dvakrát klikněte na ovládací prvek v dialogovém okně můžete přejít k deklaraci jeho naposledy implementované zprávy funkci pro zpracování.

   Pro třídy založený na knihovně ATL dialogových oken můžete vždy přejít na definici konstruktoru.

- Chcete-li zobrazit události pro ovládací prvek, ovládací prvek, zvolte **ControlEvents** tlačítko **vlastnosti** okna.

   Pokud jeden ovládací prvek má fokus v dialogovém okně, kliknete pravým tlačítkem a vyberte **přidat obslužnou rutinu události**. To umožňuje zadat třídu, ke kterému je přidání obslužné rutiny. Další informace najdete v tématu [přidání obslužné rutiny události](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > Výběr **ControlEvents** tlačítka, když je fokus dialogové okno uvádí seznam všech ovládacích prvků v poli dialogové okno, které můžete rozbalit Úprava události pro jednotlivé ovládací prvky.

- Chcete-li zobrazit zprávy pro dialogové okno, s dialogovým oknem vybrali, zvolte **zprávy** tlačítko **vlastnosti** okna.

## <a name="accelerator-keys"></a>Klávesy akcelerátoru

Níže jsou výchozí klávesové zkratky pro **editoru dialogového okna** příkazy.  

|Příkaz|klíče|Popis|
|-------------|----------|-----------------|
|Format.AlignBottoms|**CTRL** + **Shift** + **šipka dolů**|Zarovná okraje dolní části vybrané ovládací prvky s dominantního ovládacího prvku.|
|Format.AlignCenters|**Shift** + **F9**|Zarovná svisle na střed vybrané ovládací prvky s dominantního ovládacího prvku.|
|Format.AlignLefts|**CTRL** + **Shift** + **šipka vlevo**|Zarovná levé hrany vybrané ovládací prvky s dominantního ovládacího prvku.|
|Format.AlignMiddles|**F9**|Zarovná vodorovně na střed vybrané ovládací prvky s dominantního ovládacího prvku.|
|Format.AlignRights|**CTRL** + **Shift** + **šipka doprava**|Zarovná okraje pravé vybrané ovládací prvky s dominantního ovládacího prvku.|
|Format.AlignTops|**CTRL** + **Shift** + **šipka nahoru**|Zarovnává horní hrany vybrané ovládací prvky s dominantního ovládacího prvku.|
|Format.ButtonBottom|**Ctrl** + **B**|Umístí vybrané tlačítek podél dole uprostřed dialogového okna.|
|Format.ButtonRight|**Ctrl** + **R**|Umístí vybraného tlačítka v pravém horním rohu dialogového okna.|
|Format.CenterHorizontal|**Ctrl** + **Shift** + **F9**|Centra pro ovládací prvky vodorovně v dialogovém okně.|
|Format.CenterVertical|**CTRL** + **F9**|Centra pro ovládací prvky v dialogovém okně svisle.|
|Format.CheckMnemonics|**Ctrl** + **M**|Kontrola jedinečnosti klávesových zkratek.|
|Format.SizeToContent|**Shift** + **F7**|Změní velikost vybrané ovládací prvky podle text titulku.|
|Format.SpaceAcross|**ALT** + **šipka vlevo**|Rovnoměrné mezery vybrané ovládací prvky vodorovně.|
|Format.SpaceDown|**ALT** + **šipka dolů**|Rovnoměrné mezery svisle vybrané ovládací prvky.|
|Format.TabOrder|**Ctrl** + **D**|Nastaví pořadí ovládacích prvků v dialogovém okně.|
|Format.TestDialog|**Ctrl** + **T**|Spustí dialogových oken k otestování vzhled a chování.|
|Format.ToggleGuides|**Ctrl** + **G**|Přepínání mezi žádná mřížka, pokyny a Mřížka pro dialogové okno úpravy.|

- Chcete-li změnit klávesové zkratky, přejděte do nabídky **nástroje** > **možnosti**a zvolte **klávesnice** pod **prostředí** složky.

   Další informace najdete v tématu [určení a přizpůsobení klávesových zkratek](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Chcete-li změnit nastavení, přejděte do nabídky **nástroje** > **nastavení importu a exportu**.

   Dostupné možnosti v dialogových oknech, názvy a umístění příkazů nabídky se zobrazí, mohou lišit od informací uvedených v **pomáhají** v závislosti na aktivních nastaveních nebo edici.  Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Editory prostředků](../windows/resource-editors.md)<br/>
[Postupy: Vytvoření dialogového okna](../windows/creating-a-new-dialog-box.md)<br/>
[Ovládací prvky dialogového okna](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->