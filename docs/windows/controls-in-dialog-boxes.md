---
title: Dialogové okno Ovládací prvky (C++) | Dokumentace Microsoftu
ms.date: 02/15/2019
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls [C++], about dialog box controls
- dialog box controls
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
ms.openlocfilehash: 563cf73299c00413889ada2520b1bf4fcd86f2be
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023695"
---
# <a name="dialog-box-controls-c"></a>Dialogové okno Ovládací prvky (C++)

Můžete přidat ovládací prvky pole do dialogového okna pomocí **editoru dialogového okna** kartu [okno nástrojů](/visualstudio/ide/reference/toolbox) , který vám umožní vybrat ovládací prvek a přetáhněte ji do dialogových oken. Ve výchozím nastavení **nástrojů** okno bude nastaveno na automatické skrývání. Se zobrazí jako karty na levý okraj vašeho řešení při **editoru dialogového okna** je otevřený. Ale můžete připnout **nástrojů** okno na místo tak, že vyberete **automaticky skrýt** tlačítko v pravém horním rohu okna. Další informace o tom, jak řídit chování tohoto okna najdete v tématu [okno Správa](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Nejrychlejší způsob, jak přidat ovládací prvky do dialogového okna, umístění existujících ovládacích prvků nebo přesunutí ovládacích prvků z jednoho dialogového okna do jiného, je použít metodu přetahování myší. Umístění ovládacího prvku je popsaný v tečkovaná čára, dokud je přetáhnout do dialogových oken. Při přidání ovládacího prvku do dialogového okna s metodou přetažení myší, ovládací prvek dostane standardní výšku vhodné pro tento typ ovládacího prvku.

Při přidání ovládacího prvku do dialogového okna nebo jiného umístění, jeho konečné umístění může být stanoveno pomocí vodítek a okrajů, nebo zda je třeba rozložení mřížky zapnuté.

Po přidání ovládacího prvku do dialogového okna, můžete změnit vlastnosti, jako je titulek v [okno vlastností](/visualstudio/ide/reference/properties-window). Můžete také vybrat více ovládacích prvků a změňte jejich vlastnosti všechny najednou.

Další informace o **editoru dialogového okna**, naleznete v tématu Jak [přidání, úpravy nebo odstranění ovládacích prvků](adding-editing-or-deleting-controls.md), [rozložení ovládacích prvků](../windows/arrangement-of-controls-on-dialog-boxes.md), a [definovat řízení přístupu a hodnoty](../windows/defining-mnemonics-access-keys.md).

Další informace o ovládací prvky a dialogy, naleznete v tématu [třídy ovládacích prvků](../mfc/control-classes.md), [třídy dialogových oken](../mfc/dialog-box-classes.md), a [styly posuvníku](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

K dispozici ve standardní ovládací prvky **nástrojů** s výchozí události jsou:

|Název ovládacího prvku|Výchozí událost|
|---|---|
|[ovládací prvek Tlačítko](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Ovládací prvek zaškrtávací políčko](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Ovládací prvek pole se seznamem](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Ovládací prvek textové pole](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Skupinový rámeček|(není k dispozici)|
|[Ovládací prvek seznam](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Ovládací prvek přepínač](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Statický ovládací prvek textu](../mfc/reference/cstatic-class.md)|(není k dispozici)|
|[Ovládací prvek obrázek](../mfc/reference/cpictureholder-class.md)|(není k dispozici)|
|[Ovládací prvek RTF upravit 2.0](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Ovládací prvek posuvníku.](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> Další informace o používání **RichEdit 1.0** ovládacím prvkem MFC naleznete v tématu [pomocí ovládacího prvku RichEdit 1.0 s MFC](../windows/using-the-richedit-1-0-control-with-mfc.md) a [příklady pro ovládací prvek upravit bohaté](../mfc/rich-edit-control-examples.md).

[Běžných ovládacích prvků Windows](../mfc/controls-mfc.md) k dispozici v **nástrojů** poskytovat vylepšené možnosti jsou:

|Název ovládacího prvku|Výchozí událost|
|---|---|
|[Posuvník](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Ovládací prvek typu číselník](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Ovládací prvek průběh](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Ovládací prvek výměně klíče](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[Ovládací prvek seznamu](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Ovládací prvek stromu](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Ovládací prvek karty](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Animace ovládacího prvku](../mfc/using-an-animation-control.md)|ACN_START|
|[Ovládací prvek pro výběr času data](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Ovládací prvek měsíční kalendář](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[Ovládací prvek adresy IP](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Ovládacího prvku rozšířené pole se seznamem](../mfc/creating-an-extended-combo-box-control.md)||
|Vlastní ovládací prvek|TTN_GETDISPINFO|

## <a name="custom-controls"></a>Vlastní ovládací prvky

**Editoru dialogového okna** umožňuje použít existující vlastní nebo uživatelské ovládací prvky v poli šablony dialogového okna.

> [!NOTE]
> Vlastní ovládací prvky v tomto smyslu jsou by se zaměňovat s ovládacími prvky ActiveX. Ovládací prvky ActiveX se někdy označuje jako vlastní ovládací prvky OLE. Nepleťte si také, tyto ovládací prvky s ovládacími prvky vykreslované uživatelem ve Windows.

Tato funkce je určená k vám umožňují používat ovládací prvky než ty, které poskytl Windows. V době běhu ovládací prvek přidružen třídy okna (není stejná jako třída C++). Častější způsob, jak dosáhnout jednoho cíle je nainstalovat libovolný ovládací prvek, jako je statický ovládací prvek, ve vašem dialogovém okně. Pak v době spuštění v [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) fungovat, odeberte ovládacího prvku a nahraďte ji pomocí vlastního ovládacího prvku.

> [!NOTE]
> Toto je starý postup. Dnes doporučujeme ve většině případů k zápisu ovládací prvek ActiveX nebo podtřídou běžný ovládací prvek Windows.

Pro tyto ovládací prvky jste omezeni na:

- V dialogovém okně Nastavení umístění.

- Zadáním titulek.

- Název třídy ovládacího prvku Windows identifikace, protože kód vaší aplikace musí zaregistrovat ovládací prvek s tímto názvem.

- Zadáním šestnáctkovou hodnotu 32-bit, který nastaví styl ovládacího prvku.

- Nastavení rozšířené stylu.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Editor dialogových oken](../windows/dialog-editor.md)<br/>

<!--
[Adding Event Handlers for Dialog Box Controls](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->