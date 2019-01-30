---
title: Přidání ovládacího prvku do dialogového okna (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
helpviewer_keywords:
- dialog boxes [C++], adding controls to
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
- controls [C++], adding multiple
- dialog box controls [C++], size
- controls [C++], sizing
ms.assetid: b2a26d19-093f-49ca-93da-fef00dfbb381
ms.openlocfilehash: 92b644769bcbe2649d00ba68437bd474ee06dfcc
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293621"
---
# <a name="adding-a-control-to-a-dialog-box-c"></a>Přidání ovládacího prvku do dialogového okna (C++)

**Editoru dialogového okna** kartě se zobrazí v [okno nástrojů](/visualstudio/ide/reference/toolbox) když pracujete v **dialogové okno** editoru. Chcete-li přidat ovládací prvky do vaší nové dialogového okna, přetáhněte ovládací prvky z **nástrojů** do dialogového okna, kterou vytváříte. Potom můžete pohyb ovládací prvky nebo změňte jejich velikost a tvar.

K dispozici ve standardní ovládací prvky **nástrojů** jsou:

- [Ovládací prvek tlačítko](../mfc/reference/cbutton-class.md)

- [Ovládací prvek zaškrtávací políčko](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [Ovládací prvek pole se seznamem](../mfc/reference/ccombobox-class.md)

- [Ovládací prvek textové pole](../mfc/reference/cedit-class.md)

- Skupinový rámeček

- [Ovládací prvek seznam](../mfc/reference/clistbox-class.md)

- [Ovládací prvek přepínač](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [Statický ovládací prvek textu](../mfc/reference/cstatic-class.md)

- [Ovládací prvek obrázek](../mfc/reference/cpictureholder-class.md)

- [Ovládací prvek RTF upravit 2.0](../mfc/using-cricheditctrl.md)

- [Ovládací prvek posuvníku.](../mfc/reference/cscrollbar-class.md)

[Běžných ovládacích prvků Windows](../mfc/controls-mfc.md) k dispozici v **nástrojů** poskytovat vylepšené možnosti v aplikaci. Mezi ně patří:

- [Ovládací prvek posuvníku](../mfc/slider-control-styles.md)

- [Ovládací prvek typu číselník](../mfc/using-cspinbuttonctrl.md)

- [Ovládací prvek průběh](../mfc/styles-for-the-progress-control.md)

- [Ovládací prvek výměně klíče](../mfc/using-a-hot-key-control.md)

- [Ovládací prvek seznamu](../mfc/list-control-and-list-view.md)

- [Ovládací prvek stromu](../mfc/tree-control-styles.md)

- [Ovládací prvek karty](../mfc/tab-controls-and-property-sheets.md)

- [Animace ovládacího prvku](../mfc/using-an-animation-control.md)

- [Ovládací prvek pro výběr času data](../mfc/creating-the-date-and-time-picker-control.md)

- [Ovládací prvek měsíční kalendář](../mfc/month-calendar-control-examples.md)

- [Ovládací prvek adresy IP](../mfc/reference/cipaddressctrl-class.md)

- [Ovládacího prvku rozšířené pole se seznamem](../mfc/creating-an-extended-combo-box-control.md)

- [Vlastní ovládací prvek](custom-controls-in-the-dialog-editor.md)

Můžete přidat vlastní ovládací prvky do dialogového okna tak, že vyberete **vlastního ovládacího prvku** ikonu **nástrojů** a jeho přetažením na vašem dialogovém okně. Chcete-li přidat **Syslink** řídit, přidat vlastní ovládací prvek a potom změňte ovládacího prvku **třídy** vlastnost **Syslink**. To způsobí, že vlastnosti, které chcete aktualizovat a zobrazit **Syslink** vlastnosti ovládacího prvku. Informace o obálkové třídy knihovny MFC naleznete v tématu [clinkctrl –](../mfc/reference/clinkctrl-class.md).

Můžete také [přidávání ovládacích prvků ActiveX do dialogového okna vaší](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

Můžete také upravit **nástrojů** okno pro snadnější použití. Další informace najdete v tématu [používání sady nástrojů](/visualstudio/ide/using-the-toolbox).

Další informace o používání **RichEdit 1.0** ovládacím prvkem MFC naleznete v tématu [pomocí ovládacího prvku RichEdit 1.0 s MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-add-a-control-to-a-dialog-box"></a>Přidání ovládacího prvku do dialogového okna

1. Zajistěte, aby byl dialogového okna s kartami pole aktuálního dokumentu v rámci editoru. Pokud dialogové okno není aktuální dokument, nezobrazí **karta editoru dialogového okna** v **nástrojů**.

1. Na **editoru dialogového okna** karty [okno nástrojů](/visualstudio/ide/reference/toolbox), vyberte ovládací prvek pak chcete:

   - Vyberte dialogových oken v umístění, kam chcete umístit ovládací prvek. Ovládací prvek zobrazí, pokud jste vybrali.

       \- nebo –

   - Přetáhnout myší ovládacího prvku z **nástrojů** do umístění ve vašem dialogovém okně.

       \- nebo –

   - Dvakrát klikněte na panel ovládacího prvku **nástrojů** okno (se zobrazí na vašem dialogovém okně) a změna umístění ovládacího prvku do umístění, dáváte přednost.

## <a name="to-add-multiple-controls"></a>Chcete-li přidat více ovládacích prvků

1. Když podržíte **Ctrl** klíče, vyberte ovládací prvek v [okno nástrojů](/visualstudio/ide/reference/toolbox).

1. Verze **Ctrl** klíče a dialogových oken vybrat tolikrát, kolikrát chcete přidat konkrétní ovládací prvek.

1. Stisknutím klávesy **Esc** zastavit umístit ovládací prvky.

## <a name="to-size-a-control-while-you-add-it"></a>Pro nastavení velikosti ovládacího prvku během jeho přidávání

1. Vyberte ovládací prvek v [okno nástrojů](/visualstudio/ide/reference/toolbox).

1. Umístěte ukazatel myši (který se zobrazí jako různé vlasy), kde chcete levého horního rohu nový ovládací prvek bude ve vašem dialogovém okně.

1. Vyberte a podržte tlačítko myši pro ukotvení levého horního rohu ovládacího prvku v dialogovém okně pak přesuňte kurzor doprava a dolů, dokud je ovládací prvek požadovanou velikost.

   > [!NOTE]
   > Ve skutečnosti se dá ukotvit, všechny čtyři rohy požadovaný kresbě ovládací prvek. Tento postup použít jako příklad levém horním rohu.

1. Uvolněte tlačítko myši. Vyrovná ovládacího prvku do dialogového okna v zadanou velikost.

   > [!TIP]
   > Můžete změnit velikost ovládacího prvku po přetažení do dialogových oken přesunutím úchyty pro změnu velikosti ohraničení ovládacího prvku. Další informace najdete v tématu [velikosti jednotlivých ovládacích prvků](../windows/sizing-individual-controls.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Přidání obslužných rutin události pro ovládací prvky dialogového okna](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Ovládací prvky dialogových oken a typy proměnných](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)<br/>
[Třídy ovládacích prvků](../mfc/control-classes.md)<br/>
[Třídy dialogových oken](../mfc/dialog-box-classes.md)<br/>
[Styly posuvníku](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)<br/>
[Příklady ovládacích prvků pro úpravy s formátováním](../mfc/rich-edit-control-examples.md)<br/>
