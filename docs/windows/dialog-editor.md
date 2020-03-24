---
title: Editor dialogovýchC++oken ()
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
ms.openlocfilehash: 9d0f9993d81c499f67a08e5401c5e56dba7b281c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215251"
---
# <a name="dialog-editor-c"></a>Editor dialogovýchC++oken ()

**Editor dialogového okna** umožňuje vytvořit nebo upravit prostředky dialogového okna.

- Chcete-li otevřít Editor, dvakrát klikněte na soubor. RC dialogového okna v okně **prostředky** nebo přejděte na **zobrazení** nabídky > **Další Windows** > **prostředky**.

Jedním z prvních kroků při vytváření nového dialogového okna nebo šablony dialogového okna je přidání ovládacích prvků. V **editoru dialogového okna**můžete uspořádat ovládací prvky tak, aby odpovídaly určité velikosti, tvaru nebo zarovnání, nebo je můžete v dialogovém okně pracovat. Rovněž lze ovládací prvky snadno odstranit.

Dialogové okno lze uložit jako šablonu, takže je možné jej znovu použít. Rovněž lze snadno přepínat mezi návrhem dialogového okna a editací kódu, který jej implementuje.

V **editoru dialogového okna**je také možné upravit vlastnosti jednoho nebo více ovládacích prvků. Můžete změnit pořadí prvků, tj. pořadí, ve kterém ovládací prvky získají fokus při stisknutí klávesy **TAB** , nebo můžete definovat přístupová klávesa nebo kombinaci kláves, která uživatelům umožňuje vybrat ovládací prvek pomocí klávesnice.

**Editor dialogového okna** také umožňuje používat vlastní ovládací prvky, včetně ovládacích prvků ActiveX. Můžete také upravit [zobrazení formuláře](../mfc/reference/cformview-class.md), [zobrazení záznamů](../data/record-views-mfc-data-access.md)nebo [panely dialogového okna](../mfc/dialog-bars.md).

Počínaje sadou Visual Studio 2015 můžete použít **Editor dialogového okna** k definování dynamického rozložení, které určuje způsob přesunutí a změny velikosti ovládacích prvků, když uživatel změní velikost dialogového okna. Další informace najdete v tématu [dynamické rozložení](../mfc/dynamic-layout.md).

Další informace o prostředcích najdete v tématu Postup [Vytvoření dialogového okna](../windows/creating-a-new-dialog-box.md) a [ovládací prvky dialogového okna](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Při použití **editoru dialogových oken**můžete v mnoha instancích vybrat pravé tlačítko myši a zobrazit místní nabídku často používaných příkazů.

## <a name="dialog-editor-toolbar"></a>Panel nástrojů editoru dialogového okna

Panel nástrojů **editoru dialogového okna** obsahuje tlačítka pro uspořádání rozložení ovládacích prvků v dialogovém okně, například velikost a zarovnání. Tlačítka panelu nástrojů **editoru dialogového okna** odpovídají příkazům v nabídce **Formát** .

|Ikona|Význam|Ikona|Význam|
|----------|-------------|----------|-------------|
|![Tlačítko Test dialogového okna](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Dialogové okno testu|![Mezera napříč tlačítkem](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Čtečce|
|![Tlačítko Zarovnat doleva](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Zarovnat doleva|![Tlačítko rozmístit dolů](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Dolů|
|![Tlačítko Zarovnat práva](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Zarovnat práva|![Tlačítko nastavit stejnou šířku](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Nastavit stejnou šířku|
|![Zarovnat nahoru – tlačítko](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Zarovnat nahoru|![Tlačítko nastavit stejnou výšku](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Nastavit stejnou výšku|
|![Tlačítko Zarovnat dolů](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Zarovnat dolů|![Tlačítko nastavit stejnou velikost](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Nastavit stejnou velikost|
|![Tlačítko svislého středu](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Svislé|![Tlačítko pro přepnutí mřížky](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Přepnout mřížku|
|![Tlačítko vodorovně na střed](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontální|![Tlačítko Přepnout vodítka](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Přepnout vodítka|

- Chcete-li zobrazit nebo skrýt panel nástrojů **editoru dialogového okna** , přejděte do nabídky **zobrazení** > **panely nástrojů** > **editoru dialogových oken**.

Otevřete-li **Editor dialogového okna** v C++ projektu, panel nástrojů **editoru dialogového okna** se automaticky zobrazí v horní části řešení, ale pokud explicitně zavřete panel nástrojů, budete ho muset vyvolat při příštím otevření **dialogového okna Editor**. Zobrazení můžete přepnout tak, že ho vyberete ze seznamu dostupných panelů nástrojů a oken.

## <a name="switch-between-dialog-box-controls-and-code"></a>Přepínání mezi ovládacími prvky dialogového okna a kódem

V aplikacích MFC můžete dvakrát kliknout na ovládací prvky dialogového okna a přejít tak na svůj kód obslužné rutiny nebo rychle vytvořit funkci obslužné rutiny pro zástupné procedury.

Když je vybrán ovládací prvek, vyberte tlačítko **ControlEvents** nebo tlačítko **zprávy** v [okno Vlastnosti](/visualstudio/ide/reference/properties-window) k zobrazení úplného seznamu zpráv a událostí systému Windows, které jsou k dispozici pro vybranou položku. Výběrem ze seznamu můžete vytvořit nebo upravit funkce obslužných rutin.

- Chcete-li přejít na kód z **editoru dialogového okna**, dvakrát klikněte na ovládací prvek v dialogovém okně, abyste se přeskočili k deklaraci své naposledy implementované funkce zpracování zpráv.

   Pro třídy dialogového okna založené na knihovně ATL vždy přeskočíte na definici konstruktoru.

- Chcete-li zobrazit události pro ovládací prvek s vybraným ovládacím prvkem, klikněte na tlačítko **ControlEvents** v okně **vlastnosti** .

   Pokud jeden ovládací prvek má fokus v dialogovém okně, můžete kliknout pravým tlačítkem a vybrat možnost **Přidat obslužnou rutinu události**. To umožňuje zadat třídu, do které je obslužná rutina přidána. Další informace naleznete v tématu [Přidání obslužné rutiny události](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > Výběr tlačítka **ControlEvents** , když má dialogové okno fokus, zpřístupní seznam všech ovládacích prvků v dialogovém okně, které pak můžete rozbalit a upravit události pro jednotlivé ovládací prvky.

- Chcete-li zobrazit zprávy pro dialogové okno s vybraným dialogovým oknem, klikněte na tlačítko **zprávy** v okně **vlastnosti** .

## <a name="accelerator-keys"></a>Klávesy akcelerátoru

Níže jsou uvedeny výchozí klávesy akcelerátoru pro příkazy **editoru dialogového okna** .  

|Příkaz|Klíče|Popis|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl** + **SHIFT** + **šipka dolů**|Zarovnává spodní okraje vybraných ovládacích prvků s dominantním ovládacím prvkem.|
|Format.AlignCenters|**Shift** + **F9**|Zarovnává svislé středy vybraných ovládacích prvků s dominantním ovládacím prvkem.|
|Format.AlignLefts|**Ctrl** + **SHIFT** + **šipka vlevo**|Zarovná levé okraje vybraných ovládacích prvků s dominantním ovládacím prvkem.|
|Format.AlignMiddles|**Vede**|Zarovná Vodorovné středy vybraných ovládacích prvků s dominantním ovládacím prvkem.|
|Format.AlignRights|**Ctrl** + **SHIFT** + **šipka doprava**|Zarovná pravé hrany vybraných ovládacích prvků s dominantním ovládacím prvkem.|
|Format.AlignTops|**Ctrl** + **SHIFT** + **šipka nahoru**|Zarovná horní okraje vybraných ovládacích prvků s dominantním ovládacím prvkem.|
|Format.ButtonBottom|**Ctrl** + **B**|Umístí vybraná tlačítka podél dolního středu dialogového okna.|
|Format.ButtonRight|**Ctrl** + **R**|Umístí vybraná tlačítka do pravého horního rohu dialogového okna.|
|Format.CenterHorizontal|**Ctrl** + **SHIFT** + **F9**|Nacentruje ovládací prvky v dialogovém okně vodorovně.|
|Format.CenterVertical|**Ctrl** + **F9**|Nacentruje ovládací prvky v dialogovém okně svisle.|
|Format.CheckMnemonics|**Ctrl** + **M**|Kontroluje jedinečnost symbolických instrukcí.|
|Format. SizeToContent|**Shift** + **F7**|Změní velikost vybraných ovládacích prvků tak, aby odpovídaly textu titulku.|
|Format.SpaceAcross|**Alt** + **šipka vlevo**|Rovnoměrně rozmístit vybrané ovládací prvky vodorovně.|
|Format.SpaceDown|**Alt** + **šipka dolů**|Vybrané ovládací prvky se rovnoměrně rozmístí svisle.|
|Format.TabOrder|**Ctrl** + **D**|Nastaví pořadí ovládacích prvků v dialogovém okně.|
|Format.TestDialog|**Ctrl** + **t**|Spustí dialogové okno pro otestování vzhledu a chování.|
|Format.ToggleGuides|**Ctrl** + **G**|Cykly mezi žádnou mřížkou, pokyny a mřížkou pro úpravy dialogu.|

- Chcete-li změnit klávesové zkratky, přejděte na **nástroje** nabídky > **Možnosti**a ve složce **prostředí** vyberte možnost **klávesnice** .

   Další informace najdete v tématu [identifikace a přizpůsobení klávesových zkratek](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Pokud chcete změnit nastavení, přejděte na **nástroje** nabídky > **Nastavení importu a exportu**.

   Možnosti dostupné v dialogových oknech a názvy a umístění příkazů nabídky, které vidíte, se mohou lišit od toho, co je popsáno v **nápovědě** v závislosti na aktivních nastaveních nebo edici.  Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)<br/>
[Postupy: Vytvoření dialogového okna](../windows/creating-a-new-dialog-box.md)<br/>
[Ovládací prvky dialogového okna](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->
