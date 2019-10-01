---
title: Běžně přepsané členské funkce
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
ms.openlocfilehash: 51a647bb50415af71d6d148d3139f906f503ee2a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685823"
---
# <a name="commonly-overridden-member-functions"></a>Běžně přepsané členské funkce

V následující tabulce jsou uvedeny nejpravděpodobnější členské funkce, které lze přepsat v @no__t třídy odvozené od -0.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Běžně přepsané členské funkce třídy CDialog

|Členská funkce|Zpráva, na kterou reaguje|Účel přepsání|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|Inicializujte ovládací prvky dialogového okna.|
|`OnOK`|**BN_CLICKED** pro tlačítko **IDOK**|Pokud uživatel klikne na tlačítko OK, odpovězte.|
|`OnCancel`|**BN_CLICKED** pro tlačítko **IDCANCEL**|Reagovat, když uživatel klikne na tlačítko Storno.|

`OnInitDialog`, `OnOK` a `OnCancel` jsou virtuální funkce. Chcete-li je přepsat, deklarujete funkci přepsání v odvozené třídě dialogu pomocí [Průvodce třídou MFC](reference/mfc-class-wizard.md).

`OnInitDialog` se volá těsně před tím, než se zobrazí dialogové okno. Je nutné zavolat výchozí obslužnou rutinu `OnInitDialog` z přepsání, obvykle jako první akce v obslužné rutině. Ve výchozím nastavení `OnInitDialog` vrátí **hodnotu true** , aby označoval, že fokus by měl být nastaven na první ovládací prvek v dialogovém okně.

`OnOK` je obvykle přepsána pro nemodální, ale ne modální dialogová okna. Pokud přepíšete tuto obslužnou rutinu pro modální dialogové okno, zavolejte verzi základní třídy z vašeho přepsání, aby se zajistilo, že je volána `EndDialog`, nebo zavolejte `EndDialog` sami.

`OnCancel` je obvykle přepsána pro nemodální dialogová okna.

Další informace o těchto členských funkcích naleznete v tématu Třída [CDialog](../mfc/reference/cdialog-class.md) v *Referenci knihovny MFC* a diskuze o [práci s dialogovými okny v knihovně MFC](../mfc/life-cycle-of-a-dialog-box.md).

## <a name="see-also"></a>Další informace najdete v tématech

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Běžně přidávané členské funkce](../mfc/commonly-added-member-functions.md)
