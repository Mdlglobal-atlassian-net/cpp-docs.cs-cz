---
title: Běžně přepisované členské funkce
ms.date: 09/06/2019
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: f63dd6079b96181305f3207d4a1ef823df8d8ba4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907692"
---
# <a name="commonly-overridden-member-functions"></a>Běžně přepisované členské funkce

V následující tabulce jsou uvedeny nejpravděpodobnější členské funkce pro přepsání v `CDialog`odvozené třídě.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Běžně přepsané členské funkce třídy CDialog

|Členská funkce|Zpráva, na kterou reaguje|Účel přepsání|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|Inicializujte ovládací prvky dialogového okna.|
|`OnOK`|**BN_CLICKED** pro tlačítko **IDOK**|Pokud uživatel klikne na tlačítko OK, odpovězte.|
|`OnCancel`|**BN_CLICKED** pro tlačítko **IDCANCEL**|Reagovat, když uživatel klikne na tlačítko Storno.|

`OnInitDialog`, `OnOK` a`OnCancel` jsou virtuální funkce. Chcete-li je přepsat, deklarujete funkci přepsání v odvozené třídě dialogu pomocí [Průvodce třídou MFC](reference/mfc-class-wizard.md).

`OnInitDialog`se volá těsně před tím, než se zobrazí dialogové okno. Musíte zavolat výchozí `OnInitDialog` obslužnou rutinu z vašeho přepsání, obvykle jako první akce v obslužné rutině. Ve výchozím nastavení `OnInitDialog` vrátí **hodnotu true** k označení, že fokus by měl být nastaven na první ovládací prvek v dialogovém okně.

`OnOK`je obvykle přepsána pro nemodální, ale ne modální dialogová okna. Pokud přepíšete tuto obslužnou rutinu pro modální dialogové okno, zavolejte verzi základní třídy z vašeho přepsání, aby se `EndDialog` zajistilo, že je `EndDialog` volána – nebo zavolejte sami.

`OnCancel`je obvykle přepsána pro nemodální dialogová okna.

Další informace o těchto členských funkcích naleznete v tématu Třída [CDialog](../mfc/reference/cdialog-class.md) v *Referenci knihovny MFC* a diskuze o [životním cyklu dialogového okna](../mfc/life-cycle-of-a-dialog-box.md).

## <a name="see-also"></a>Viz také:

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Běžně přidávané členské funkce](../mfc/commonly-added-member-functions.md)
