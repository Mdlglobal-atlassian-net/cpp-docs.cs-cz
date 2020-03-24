---
title: Ovládací prvky dialogového oknaC++() | Microsoft Docs
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
ms.openlocfilehash: c79021387de2c8bc8f7f106a93797b7efb07d6df
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160408"
---
# <a name="dialog-box-controls-c"></a>Ovládací prvky dialogovýchC++oken ()

Ovládací prvky můžete přidat do dialogového okna pomocí karty **Editor dialogového** okna v [okně panelu nástrojů](/visualstudio/ide/reference/toolbox) , která umožňuje výběr požadovaného ovládacího prvku a jeho přetažením do dialogového okna. Ve výchozím nastavení je okno sady **nástrojů** nastaveno na automatické skrývání. Zobrazuje se jako karta na levém okraji vašeho řešení, když je otevřen **Editor dialogových oken** . Můžete však připnout okno **sady nástrojů** na pozici tak, že vyberete tlačítko pro **automatické skrývání** v pravém horním rohu okna. Další informace o tom, jak řídit chování tohoto okna, najdete v tématu [Správa oken](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Nejrychlejší způsob, jak přidat ovládací prvky do dialogového okna, přemístit existující ovládací prvky nebo přesunout ovládací prvky z jednoho dialogového okna na jiný, je použít metodu přetažení. Pozice ovládacího prvku je potažena na tečkované spojnici, dokud není vložena do dialogového okna. Při přidání ovládacího prvku do dialogového okna s metodou přetažení je ovládacímu prvku přiřazena standardní výška odpovídající tomuto typu ovládacího prvku.

Když přidáte ovládací prvek do dialogového okna nebo změníte jeho umístění, jeho konečné umístění může být určeno vodítky nebo okraji nebo zda máte zapnutou mřížku rozložení.

Po přidání ovládacího prvku do dialogového okna můžete změnit vlastnosti, jako je jeho titulek v [okně Vlastnosti](/visualstudio/ide/reference/properties-window). Můžete také vybrat více ovládacích prvků a změnit jejich vlastnosti najednou.

Další informace o **editoru dialogového okna**naleznete v tématu Jak [Přidat, upravit nebo odstranit ovládací prvky](adding-editing-or-deleting-controls.md), [ovládací prvky rozložení](../windows/arrangement-of-controls-on-dialog-boxes.md)a [definovat přístup a hodnoty řízení](../windows/defining-mnemonics-access-keys.md).

Další informace o ovládacích prvcích a dialogách naleznete v tématech [třídy ovládacích](../mfc/control-classes.md)prvků, [třídy dialogových oken](../mfc/dialog-box-classes.md)a [posouvání styly](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

Standardní ovládací prvky, které jsou k dispozici v **panelu nástrojů** s výchozími událostmi:

|Název ovládacího prvku|Výchozí událost|
|---|---|
|[Ovládací prvek tlačítko](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Ovládací prvek zaškrtávací políčko](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Ovládací prvek pole se seznamem](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Upravit ovládací prvek](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Skupinový rámeček|(nelze použít)|
|[Ovládací prvek seznamu](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Ovládací prvek přepínačů](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Ovládací prvek statického textu](../mfc/reference/cstatic-class.md)|(nelze použít)|
|[Ovládací prvek obrázek](../mfc/reference/cpictureholder-class.md)|(nelze použít)|
|[Ovládací prvek s bohatou úpravou 2,0](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Ovládací prvek posuvníku](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> Další informace o použití ovládacího prvku **richedit 1,0** s knihovnou MFC naleznete v tématu [použití ovládacího prvku RichEdit 1,0 s](../windows/using-the-richedit-1-0-control-with-mfc.md) [Příklady ovládacích prvků MFC a Rich Edit](../mfc/rich-edit-control-examples.md).

[Běžné ovládací prvky systému Windows](../mfc/controls-mfc.md) , které jsou k dispozici v **sadě nástrojů** pro zajištění vyšší funkčnosti:

|Název ovládacího prvku|Výchozí událost|
|---|---|
|[Ovládací prvek posuvníku](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Otočný ovládací prvek](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Průběh – ovládací prvek](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Klávesová zkratka](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[Ovládací prvek seznamu](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Ovládací prvek strom](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Ovládací prvek karta](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Ovládací prvek animace](../mfc/using-an-animation-control.md)|ACN_START|
|[Ovládací prvek pro výběr data a času](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Ovládací prvek měsíční kalendář](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[Řízení IP adres](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Rozšířený ovládací prvek pole se seznamem](../mfc/creating-an-extended-combo-box-control.md)||
|Vlastní ovládací prvek|TTN_GETDISPINFO|

## <a name="custom-controls"></a>Vlastní ovládací prvky

**Editor dialogového okna** umožňuje použít existující vlastní nebo uživatelské ovládací prvky v šabloně dialogového okna.

> [!NOTE]
> Vlastní ovládací prvky v tomto smyslu se nepleťou s ovládacími prvky ActiveX. Ovládací prvky ActiveX byly někdy označovány jako vlastní ovládací prvky OLE. Nepleťte si také tyto ovládací prvky s ovládacími prvky vykreslenými vlastníkem ve Windows.

Tato funkce je určená k tomu, aby vám umožnila používat jiné ovládací prvky než ty, které poskytuje Windows. V době běhu je ovládací prvek spojen s třídou okna (není totéž jako C++ třída). Častým způsobem, jak dosáhnout stejné úlohy, je instalace libovolného ovládacího prvku, jako je například statický ovládací prvek, v dialogovém okně. Potom v době spuštění ve funkci [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) odeberte tento ovládací prvek a nahraďte ho vlastním ovládacím prvkem.

> [!NOTE]
> Jedná se o starou techniku. V současné době jste ve většině případů doporučili psát ovládací prvek ActiveX nebo podtřídu běžný ovládací prvek systému Windows.

Pro tyto vlastní ovládací prvky je omezeno na:

- Nastavení umístění v dialogovém okně.

- Zadání titulku.

- Určení názvu třídy Windows ovládacího prvku, protože kód vaší aplikace musí ovládací prvek zaregistrovat pomocí tohoto názvu.

- Zadání 32 hexadecimální hodnoty, která nastaví styl ovládacího prvku.

- Nastavení rozšířeného stylu

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor dialogových oken](../windows/dialog-editor.md)

<!--
[Adding Event Handlers for Dialog Box Controls](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->
