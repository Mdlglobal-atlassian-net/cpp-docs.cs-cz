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
ms.openlocfilehash: fef4a7f0d4c785a40ea946127d8e3c84c797e1aa
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336693"
---
# <a name="dialog-editor-c"></a>Editor dialogových oken (C++)

**Dialogové okno** editor umožňuje vytvoření nebo úpravu prostředků dialogových oken. Otevřete editor dialogového okna poklikáním na soubor .rc dialogu v **zobrazení prostředků** okno (**zobrazení** > **zobrazení prostředků**). Všimněte si, že **zobrazení prostředků** není k dispozici ve verzích Express.

Jedním z prvních kroků při vytváření nového dialogového okna (nebo šablony dialogového okna) je přidání ovládacích prvků dialogového okna. V **dialogové okno** editor, je možné uspořádat ovládací prvky podle určité velikosti, tvaru nebo zarovnání, nebo je můžete přesouvat přibližně pro práci v dialogovém okně. Rovněž lze ovládací prvky snadno odstranit.

Dialogové okno lze uložit jako šablonu, takže je možné jej znovu použít. Rovněž lze snadno přepínat mezi návrhem dialogového okna a editací kódu, který jej implementuje.

V Editoru dialogového okna je rovněž možné upravovat vlastnosti jednoho nebo více ovládacích prvků. Můžete změnit pořadí ovládacích prvků, to znamená, když pořadí, ve kterém ovládací prvky získávají zaměřit **kartu** stisknutí klávesy, nebo lze definovat přístupovou klávesu (kombinaci kláves), který umožňuje uživatelům vybrat ovládací prvek pomocí klávesnice.

**Dialogové okno** editor také umožňuje použití vlastních ovládacích prvků, včetně ovládacích prvků ActiveX. Kromě toho můžete upravit [zobrazení formuláře](../mfc/reference/cformview-class.md), [zobrazení záznamů](../data/record-views-mfc-data-access.md), nebo [dialogové pruhy](../mfc/dialog-bars.md).

Od verze Visual Studio 2015, můžete použít editor dialogového okna pro definování dynamického rozložení, které určují, jak ovládací prvky přesunutí a změna velikosti, když uživatel změní dialogové okno. Další informace najdete v tématu [dynamické rozložení](../mfc/dynamic-layout.md).

- [Postupy: Vytvoření dialogového okna](../windows/creating-a-new-dialog-box.md)

- [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)

   > [!TIP]
   > Při použití **dialogové okno** editoru v mnoha případech můžete vybrat pravé tlačítko myši zobrazit místní nabídku s často používanými příkazy.

## <a name="dialog-editor-toolbar"></a>Panel nástrojů editoru dialogového okna

Když otevřete **dialogové okno** editoru v projektu v jazyce C++ **editoru dialogového okna** nástrojů se automaticky zobrazí v horní části vašeho řešení.

|Ikona|Význam|Ikona|Význam|
|----------|-------------|----------|-------------|
|![Tlačítko Testovat Dialog](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Testovací dialogové okno|![Místo přes tlačítko](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Mezi|
|![Zarovnat doleva tlačítko](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Zarovnat doleva|![Tlačítko místo dolů](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Dolů|
|![Zarovnat práva tlačítko](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Zarovnat doprava|![Ujistěte se stejnou šířku tlačítka](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Nastavit stejnou šířku|
|![Zarovnat horní tlačítko](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Zarovnat nahoru|![Ujistěte se stejnou výškou tlačítko](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Stejná výška|
|![Zarovnat DNA tlačítko](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Zarovnat dolů|![Ujistěte se stejnou velikostí tlačítko](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Nastavit stejnou velikost|
|![Tlačítko svisle Center](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Svisle|![Přepínací tlačítko mřížky](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Přepnout mřížku|
|![Vodorovná tlačítka Center](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Vodorovná|![Tlačítko průvodce přepínací tlačítko](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Průvodce přepínací tlačítko|

**Editoru dialogového okna** nástrojů obsahuje tlačítka pro uspořádání rozložení ovládacích prvků v dialogovém okně třeba velikost a zarovnání. **Editor dialogových oken** tlačítka na panelu nástrojů odpovídají příkazy na **formátu** nabídky.

Pokud pracujete s **dialogové okno** editoru můžete přepínat zobrazení **editoru dialogového okna** nástrojů tak, že ho vyberete ze seznamu dostupných panelů nástrojů a oken.

- Zobrazení nebo skrytí panelu nástrojů editoru dialogového okna na **zobrazení** nabídce vyberte možnost **panely nástrojů**, klikněte na tlačítko **editoru dialogového okna** z podnabídky.

   > [!NOTE]
   > **Editoru dialogového okna** nástrojů je ve výchozím nastavení zobrazí, když otevřete zdroj dialogového okna v editoru dialogového okna; nicméně, pokud explicitně Zavřít panel nástrojů, budete muset ho vyvolat při příštím otevření zdroj dialogového okna.

## <a name="switch-between-dialog-box-controls-and-code"></a>Přepínání mezi ovládacími prvky dialogového okna a kódem

V aplikacích MFC můžete dvakrát kliknout na dialogové okno Ovládací prvky pro přechod na svůj kód obslužné rutiny nebo k rychlému vytvoření zástupné procedury funkcí obslužných rutin.

Ovládací prvek vybraný, klikněte **ControlEvents** tlačítko nebo **zprávy** tlačítko [okno vlastností](/visualstudio/ide/reference/properties-window) Chcete-li zobrazit úplný seznam událostí a zpráv Windows k dispozici pro vybranou položku. Zvolte ze seznamu a vytvořit nebo upravit funkce obslužné rutiny.

- Můžete přejít ke kódu z editoru dialogového okna, dvakrát klikněte na ovládací prvek v dialogovém okně můžete přejít k deklaraci jeho naposledy implementované zprávy funkci pro zpracování. (Pro třídy založený na knihovně ATL dialogových oken, můžete vždy přejít na definici konstruktoru.)

- Chcete-li zobrazit události pro ovládací prvek, ovládací prvek, zvolte **ControlEvents** tlačítko [okno vlastností](/visualstudio/ide/reference/properties-window).

   > [!NOTE]
   > Výběr **ControlEvents** tlačítko, kdy *dialogové okno* má fokus zpřístupňuje seznam všech ovládacích prvků v poli dialogové okno, které můžete rozbalit Úprava události pro jednotlivé ovládací prvky.

   Pokud jeden ovládací prvek má fokus v dialogovém okně, pravým tlačítkem myši a vybrat můžete **přidat obslužnou rutinu události** z místní nabídky. To umožňuje zadat třídu, ke kterému je přidání obslužné rutiny. Další informace najdete v tématu [přidání obslužné rutiny události](../ide/adding-an-event-handler-visual-cpp.md).

- Chcete-li zobrazit zprávy pro dialogové okno, s dialogovým oknem vybrali, zvolte **zprávy** tlačítko [okno Vlastnosti](/visualstudio/ide/reference/properties-window).

## <a name="accelerator-keys"></a>Klávesy akcelerátoru

V následující tabulce jsou výchozí klávesy akcelerátoru pro editor dialogového okna příkazy. Chcete-li změnit klávesové zkratky, vyberte **možnosti** na **nástroje** nabídky, klikněte na tlačítko **klávesnice** pod **prostředí** složky. Další informace najdete v tématu [určení a přizpůsobení klávesových zkratek](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Dostupné možnosti v dialogových oknech, názvy a umístění příkazů, které vidíte, mohou lišit od informací uvedených v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Příkaz|klíče|Popis|
|-------------|----------|-----------------|
|Format.AlignBottoms|**CTRL** + **Shift** + **šipka dolů**|Zarovnává dolní okraje vybrané ovládací prvky s dominantního ovládacího prvku|
|Format.AlignCenters|**Shift** + **F9**|Zarovná svisle na střed vybrané ovládací prvky s dominantního ovládacího prvku|
|Format.AlignLefts|**CTRL** + **Shift** + **šipka vlevo**|Zarovná levé hrany vybrané ovládací prvky s dominantního ovládacího prvku|
|Format.AlignMiddles|**F9**|Zarovná vodorovně na střed vybrané ovládací prvky s dominantního ovládacího prvku|
|Format.AlignRights|**CTRL** + **Shift** + **šipka doprava**|Zarovná okraje pravé vybrané ovládací prvky s dominantního ovládacího prvku|
|Format.AlignTops|**CTRL** + **Shift** + **šipka nahoru**|Zarovnává horní hrany vybrané ovládací prvky s dominantního ovládacího prvku|
|Format.ButtonBottom|**Ctrl** + **B**|Umístí vybrané tlačítek podél dole uprostřed dialogového okna|
|Format.ButtonRight|**Ctrl** + **R**|Umístí vybraného tlačítka v pravém horním rohu dialogového okna|
|Format.CenterHorizontal|**Ctrl** + **Shift** + **F9**|Centra pro ovládací prvky vodorovně do dialogových oken|
|Format.CenterVertical|**CTRL** + **F9**|Centra pro ovládací prvky v dialogovém okně svisle|
|Format.CheckMnemonics|**Ctrl** + **M**|Kontrola jedinečnosti klávesových zkratek|
|Format.SizeToContent|**Shift** + **F7**|Změní velikost vybrané ovládací prvky podle text titulku|
|Format.SpaceAcross|**ALT** + **šipka vlevo**|Rovnoměrné mezery vybrané ovládací prvky vodorovně|
|Format.SpaceDown|**ALT** + **šipka dolů**|Rovnoměrné mezery vybrané ovládací prvky svisle|
|Format.TabOrder|**Ctrl** + **D**|Nastaví pořadí ovládacích prvků v dialogovém okně|
|Format.TestDialog|**Ctrl** + **T**|Spustí dialogových oken k otestování vzhled a chování|
|Format.ToggleGuides|**Ctrl** + **G**|Přepínání mezi žádná mřížka, pokyny a Mřížka pro dialogové okno Úpravy|

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Postupy: Vytvoření prostředku](../windows/how-to-create-a-resource.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)<br/>
[Třídy ovládacích prvků](../mfc/control-classes.md)<br/>
[Třídy dialogových oken](../mfc/dialog-box-classes.md)<br/>
[Ovládací prvky dialogových oken a typy proměnných](../ide/dialog-box-controls-and-variable-types.md)