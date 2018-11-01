---
title: Výchozí události ovládacích prvků
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls [C++], events
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
ms.openlocfilehash: 8cd0102be240bc98cf7900653b8fbb714e2a99a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520403"
---
# <a name="default-control-events"></a>Výchozí události ovládacích prvků

Následující názvy ovládacích prvků mají související výchozí události:

|Název ovládacího prvku|Výchozí událost|
|------------------|-------------------|
|Animace|ACN_START|
|Zaškrtávací políčko|BN_CLICKED|
|Pole se seznamem|CBN_SELCHANGE|
|Vlastní|TTN_GETDISPINFO|
|Výběr data a času|DTN_DATETIMECHANGE –|
|Textové pole|EN_CHANGE|
|Skupinový rámeček|(Není k dispozici)|
|Klávesová zkratka|NM_OUTOFMEMORY –|
|IP adresa|IPN_FIELDCHANGED|
|Seznam|LVN_ITEMCHANGE|
|Pole se seznamem|LBN_SELCHANGE|
|Měsíční kalendář|MCN_SELCHANGE|
|Ovládací prvek obrázek|(Není k dispozici)|
|Průběh|NM_CUSTOMDRAW|
|Příkazové tlačítko|BN_CLICKED|
|Přepínací tlačítko|BN_CLICKED|
|Pro úpravy s formátováním|EN_CHANGE|
|Posuvník|NM_THEMECHANGED|
|Posuvník|NM_CUSTOMDRAW|
|Typu číselník|UDN_DELTAPOS|
|Statický Text|(Není k dispozici)|
|Tabulátor|TCN_SELCHANGE|
|Strom|TVN_SELCHANGE|

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Definování členských proměnných pro ovládací prvky dialogového okna](../windows/defining-member-variables-for-dialog-controls.md)<br/>
[Typy zpráv přidružených k objektům uživatelského rozhraní](../mfc/reference/message-types-associated-with-user-interface-objects.md)<br/>
[Úpravy obslužné rutiny zpráv](../mfc/reference/editing-a-message-handler.md)<br/>
[Definování obslužné rutiny zpráv pro zrcadlené zprávy](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)<br/>
[Deklarace proměnné založené na nové třídě ovládacího prvku](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)<br/>
[Přepisování virtuální funkce](../ide/overriding-a-virtual-function-visual-cpp.md)