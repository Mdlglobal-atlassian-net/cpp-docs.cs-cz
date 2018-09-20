---
title: Běžně přepisované členské funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aabc88db4fcb2a484ca44feea8fcdf7727e23a16
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431408"
---
# <a name="commonly-overridden-member-functions"></a>Běžně přepisované členské funkce

Následující tabulka uvádí nejvíce pravděpodobně členské funkce přepsat v vaše `CDialog`-odvozené třídy.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Běžně přepisované členské funkce CDialog – třída

|Členská funkce|Zpráva, která reaguje na|Účelem přepsání|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**NEZAVĚSÍTE**|Inicializujte ovládací prvky dialogových oken.|
|`OnOK`|**BN_CLICKED** pro tlačítko **IDOK**|Reagujte, když uživatel klikne na tlačítko OK.|
|`OnCancel`|**BN_CLICKED** pro tlačítko **IDCANCEL**|Reagujte, když uživatel klikne na tlačítko Storno.|

`OnInitDialog`, `OnOK`, a `OnCancel` jsou virtuální funkce. K jejich přepsání, deklarujete přepisující funkce v třídě odvozené dialogového okna pomocí [okno vlastností](/visualstudio/ide/reference/properties-window).

`OnInitDialog` je volána těsně před plánovaným zobrazí dialogové okno. Je nutné volat výchozí `OnInitDialog` obslužnou rutinu z přepsání – obvykle jako první akci v obslužné rutině. Ve výchozím nastavení `OnInitDialog` vrátí **TRUE** k označení, že fokusu musí být nastaveno na první ovládací prvek v dialogovém okně.

`OnOK` Obvykle je přepsána pro nemodální, ale ne modální dialogová okna. Pokud přepíšete této obslužné rutiny pro modální dialogové okno, zavolejte verzi základní třídy z přepsání – Chcete-li zajistit `EndDialog` se nazývá – nebo se telefonicky `EndDialog` sami.

`OnCancel` Obvykle je přepsána pro nemodální dialogová okna.

Další informace o těchto funkcích najdete v tématu třídy [CDialog](../mfc/reference/cdialog-class.md) v *odkaz knihovny MFC* a diskuse o [životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md).

## <a name="see-also"></a>Viz také

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Běžně přidávané členské funkce](../mfc/commonly-added-member-functions.md)
