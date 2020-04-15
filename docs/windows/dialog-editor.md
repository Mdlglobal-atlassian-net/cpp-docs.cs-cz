---
title: Editor dialogů (C++)
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
ms.openlocfilehash: f1544d3a8e14f9373e21b77d888860d24ab1ed6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370291"
---
# <a name="dialog-editor-c"></a>Editor dialogů (C++)

**Editor dialogů** umožňuje vytvářet nebo upravovat prostředky dialogového okna.

- Chcete-li editor otevřít, poklepejte na soubor RC dialogového okna v okně **Zobrazení zdrojů** nebo přejděte do nabídky **Zobrazit** > jiné**zobrazení prostředků systému****Windows** > .

Jedním z prvních kroků při vytváření nového dialogového okna nebo šablony dialogového okna je přidání ovládacích prvků. V **Editoru dialogů**můžete uspořádat ovládací prvky tak, aby odpovídaly určité velikosti, tvaru nebo zarovnání, nebo je můžete přesunout a pracovat v dialogovém okně. Rovněž lze ovládací prvky snadno odstranit.

Dialogové okno lze uložit jako šablonu, takže je možné jej znovu použít. Rovněž lze snadno přepínat mezi návrhem dialogového okna a editací kódu, který jej implementuje.

Je také možné upravit vlastnosti jednoho nebo více ovládacích prvků v **Editoru dialogů**. Můžete změnit pořadí polí, to znamená pořadí, ve kterém ovládací prvky získají fokus při stisknutí **klávesy Tab,** nebo můžete definovat přístupovou klávesu nebo kombinaci kláves, která uživatelům umožňuje zvolit ovládací prvek pomocí klávesnice.

**Editor dialogů** také umožňuje používat vlastní ovládací prvky, včetně ovládacích prvků ActiveX. Můžete také upravit [zobrazení formuláře](../mfc/reference/cformview-class.md), zobrazení [záznamů](../data/record-views-mfc-data-access.md)nebo [dialogové čáry](../mfc/dialog-bars.md).

Počínaje Visual Studio 2015 můžete pomocí **Editoru dialogů** definovat dynamická rozložení, která určují, jak se ovládací prvky přesouvají a měňmají velikost, když uživatel změní velikost dialogového okna. Další informace naleznete v [tématu Dynamické rozložení](../mfc/dynamic-layout.md).

Další informace o zdrojích naleznete v [tématu Vytvoření dialogového okna](../windows/creating-a-new-dialog-box.md) a [ovládacích prvků dialogového okna](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Při použití **Editoru dialogů**můžete v mnoha případech vybrat pravým tlačítkem myši a zobrazit místní nabídku často používaných příkazů.

## <a name="dialog-editor-toolbar"></a>Panel nástrojů Editor dialogů

Panel nástrojů **Editor dialogů** obsahuje tlačítka pro uspořádání rozložení ovládacích prvků v dialogovém okně, například velikost a zarovnání. **Tlačítka panelu** nástrojů Editor dialogů odpovídají příkazům v nabídce **Formát.**

|Ikona|Význam|Ikona|Význam|
|----------|-------------|----------|-------------|
|![Tlačítko Testovat dialog](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorDialog")|Dialogové okno Testovat|![Tlačítko Mezera napříč](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Přes|
|![Tlačítko Zarovnat doleva](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Zarovnat doleva|![Tlačítko Space Down](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Dolů|
|![Tlačítko Zarovnat práva](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Zarovnat práva|![Tlačítko Vytvořit stejnou šířku](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Vytvořit stejnou šířku|
|![Tlačítko Zarovnat horní části](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Zarovnat horní části|![Tlačítko Vytvořit stejnou výšku](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Vytvořit stejnou výšku|
|![Tlačítko Zarovnat dna](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Zarovnat dna|![Tlačítko Vytvořit stejnou velikost](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Vytvořit stejnou velikost|
|![Střed svislé tlačítko](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Svisle|![Tlačítko Přepnout mřížku](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Přepnout mřížku|
|![Tlačítko Na střed vodorovně](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontální")|Vodorovně|![Tlačítko Přepnout vodítka](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Přepnout vodítka|

- Chcete-li zobrazit nebo skrýt panel nástrojů **Editor dialogů,** přejděte do nabídky **Zobrazit** > **panely nástrojů** > **Dialog Editor**.

Když otevřete **Editor dialogů** v projektu jazyka C++, panel nástrojů **Editor dialogů** se automaticky zobrazí v horní části řešení, ale pokud explicitně zavřete panel nástrojů, budete ho muset vyvolat při příštím otevření **Editoru dialogů**. Jeho zobrazení můžete přepínat tak, že jej vyberete ze seznamu dostupných panelů nástrojů a oken.

## <a name="switch-between-dialog-box-controls-and-code"></a>Přepínání mezi ovládacími prvky dialogového okna a kódem

V aplikacích knihovny MFC můžete poklepáním na ovládací prvky dialogového okna přejít na jejich kód obslužné rutiny nebo rychle vytvořit funkce obslužné rutiny se zakázaným insvícení protokolu.

S vybraným ovládacím prvkem vyberte tlačítko **ControlEvents** nebo **tlačítko Zprávy** v [okně Vlastnosti,](/visualstudio/ide/reference/properties-window) chcete-li zobrazit úplný seznam zpráv a událostí systému Windows dostupných pro vybranou položku. Vyberte ze seznamu a vytvořte nebo upravte funkce obslužné rutiny.

- Chcete-li přejít na kód z **editoru dialogů**, poklepejte na ovládací prvek v dialogovém okně a přejděte na deklaraci pro naposledy implementovanou funkci zpracování zpráv.

   Pro třídy dialogu založené na atl vždy přejít na definici konstruktoru.

- Chcete-li zobrazit události ovládacího prvku s vybraným ovládacím prvkem, zvolte tlačítko **ControlEvents** v okně **Vlastnosti.**

   Pokud je v dialogovém okně fokus jednoho ovládacího prvku, můžete klepnout pravým tlačítkem myši a vybrat **přidat obslužnou rutinu události**. To umožňuje určit třídu, do které je přidánobslužná rutina. Další informace naleznete [v tématu Přidání obslužné rutiny události](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > Výběr **emisi ControlEvents,** když má dialogové okno fokus, zobrazí seznam všech ovládacích prvků v dialogovém okně, které pak můžete rozbalit a upravit události pro jednotlivé ovládací prvky.

- Chcete-li zobrazit zprávy pro dialogové okno s vybraným dialogovým oknem, zvolte tlačítko **Zprávy** v okně **Vlastnosti.**

## <a name="accelerator-keys"></a>Klávesy akcelerátoru

Níže jsou uvedeny výchozí klávesy akcelerátoru pro příkazy **Editoru dialogů.**  

|Příkaz|Klíče|Popis|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl** + **Shift** + **šipka dolů**|Zarovná spodní okraje vybraných ovládacích prvků s dominantním ovládacím prvkem.|
|Format.AlignCenters|**Posun** + **F9**|Zarovná svislé středy vybraných ovládacích prvků s dominantním ovládacím prvkem.|
|Format.AlignLefts|**Ctrl** + **Shift** + **šipka doleva**|Zarovná levé okraje vybraných ovládacích prvků s dominantním ovládacím prvkem.|
|Format.AlignMiddles|**F9**|Zarovná vodorovné středy vybraných ovládacích prvků s dominantním ovládacím prvkem.|
|Format.AlignRights|**Ctrl** + **Shift** + **šipka doprava**|Zarovná pravé okraje vybraných ovládacích prvků s dominantním ovládacím prvkem.|
|Format.AlignTops|**Ctrl** + **Shift** + **Šipka nahoru**|Zarovná horní okraje vybraných ovládacích prvků s dominantním ovládacím prvkem.|
|Format.ButtonBottom|**Ctrl** + **B**|Umístí vybraná tlačítka podél dolního středu dialogového okna.|
|Format.ButtonRight|**Ctrl** + **R**|Umístí vybraná tlačítka do pravého horního rohu dialogového okna.|
|Format.CenterHorizontal|**Ctrl** + **Shift** + **F9**|Vystředí ovládací prvky vodorovně v dialogovém okně.|
|Format.CenterVertical|**Ctrl** + **F9**|Vystředí ovládací prvky svisle v dialogovém okně.|
|Format.CheckMnemonics|**Ctrl** + **M**|Kontroluje jedinečnost mnemotechnické pomůcky.|
|Format.SizeToContent|**Posun** + **F7**|Změní velikost vybraných ovládacích prvku tak, aby odpovídaly textu titulku.|
|Format.SpaceAcross|**Alt** + **šipka doleva**|Rovnoměrně rozmístí vybrané ovládací prvky vodorovně.|
|Format.SpaceDown|**Alt**Alt**šipka dolů**  + |Rovnoměrně rozmístí vybrané ovládací prvky svisle.|
|Format.TabOrder|**Ctrl** + **D**|Nastaví pořadí ovládacích prvků v dialogovém okně.|
|Format.TestDialog|**Ctrl** + **T**|Spustí dialogové okno pro testování vzhledu a chování.|
|Format.ToggleGuides|**Ctrl** + **G**|Cykly mezi žádnou mřížkou, pokyny a mřížkou pro úpravy dialogů.|

- Chcete-li změnit klávesové zkratky, přejděte do nabídky**Možnosti** **nástrojů** > a ve složce **Životní prostředí** zvolte **Klávesnice.**

   Další informace naleznete [v tématu Identifikace a přizpůsobení klávesových zkratek](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Chcete-li změnit nastavení, přejděte do nabídky **Nástroje** > **pro import a export nastavení**.

   Možnosti dostupné v dialogových oknech a názvy a umístění příkazů nabídek, které vidíte, se mohou lišit od toho, co je popsáno v **nápovědě** v závislosti na aktivním nastavení nebo edici.  Další informace naleznete [v tématu Přizpůsobení prostředí IDE sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)<br/>
[Postup: Vytvoření dialogového okna](../windows/creating-a-new-dialog-box.md)<br/>
[Ovládací prvky dialogového okna](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->
