---
title: Běžně přepisované členské funkce | Microsoft Docs
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
ms.openlocfilehash: ed090057394c385dd12825864c5de9ff7d079e29
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="commonly-overridden-member-functions"></a>Běžně přepisované členské funkce
Následující tabulka uvádí s největší pravděpodobností členské funkce pro přepsání v vaší `CDialog`-odvozené třídy.  
  
### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Běžně přepisované členské funkce CDialog – třída  
  
|Členská funkce|Zprávy, kterou odpoví na|Účelem přepsání|  
|---------------------|----------------------------|-----------------------------|  
|`OnInitDialog`|**WM_INITDIALOG**|Inicializujte ovládací prvky dialogových oken.|  
|`OnOK`|**BN_CLICKED** pro tlačítko **IDOK**|Reagovat, když uživatel klikne na tlačítko OK.|  
|`OnCancel`|**BN_CLICKED** pro tlačítko **IDCANCEL**|Reagovat, když uživatel klikne na tlačítko Storno.|  
  
 `OnInitDialog`, `OnOK`, a `OnCancel` jsou virtuální funkce. Pokud chcete přepsat, je, deklarovat přepsání funkce pomocí třídy odvozené dialogu [vlastnosti – okno](/visualstudio/ide/reference/properties-window).  
  
 `OnInitDialog` je volána těsně před se zobrazí dialogové okno. Je třeba volat výchozí `OnInitDialog` obslužnou rutinu na základě přepsání – obvykle jako první akcí v obslužné rutině. Ve výchozím nastavení `OnInitDialog` vrátí **TRUE** indikující, že fokus měla být nastavena na první ovládací prvek v dialogovém okně.  
  
 `OnOK` Obvykle přepsána u nemodální, ale není modální dialogová okna. Pokud přepíšete této obslužné rutiny pro modální dialogové okno, zavolejte na verzi základní třída z přepsání – zajistit, aby `EndDialog` nazývá – nebo volání `EndDialog` sami.  
  
 `OnCancel` Obvykle přepsána u nemodální dialogová okna.  
  
 Další informace informace o těchto funkcích najdete v tématu třídy [CDialog](../mfc/reference/cdialog-class.md) v *odkaz knihovny MFC* a diskuzi na [životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md).  
  
## <a name="see-also"></a>Viz také  
 [Dialogová okna](../mfc/dialog-boxes.md)   
 [Běžně přidávané členské funkce](../mfc/commonly-added-member-functions.md)
