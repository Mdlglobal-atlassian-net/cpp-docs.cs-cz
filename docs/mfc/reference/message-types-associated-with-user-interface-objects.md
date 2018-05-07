---
title: Zpráva typy přidružené objekty uživatelského rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.uiobject.msgs
dev_langs:
- C++
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14a2309556ca6c5204247ccbe916aebe472a1da1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="message-types-associated-with-user-interface-objects"></a>Typy zpráv přidružených k objektům uživatelského rozhraní
V následující tabulce jsou uvedeny typy objektů, se kterými pracujete a typy zpráv s nimi spojených.  
  
### <a name="user-interface-objects-and-associated-messages"></a>Objekty uživatelského rozhraní a související zprávy  
  
|ID objektu|Zprávy|  
|---------------|--------------|  
|Název třídy představující obsahující okno|Zprávy systému Windows [CWnd](../../mfc/reference/cwnd-class.md)-odvozené třídy: dialogové okno, okno, podřízeného okna, podřízeného okna MDI nebo nejhornější rámce okna.|  
|Identifikátor nabídky nebo akcelerátoru|-   **PŘÍKAZ** zprávy (spustí funkce programu).<br />-   **UPDATE_COMMAND_UI** zprávy (dynamicky aktualizuje položky nabídky).|  
|Identifikátor ovládacího prvku|Oznamující zprávy pro ovládací prvek pro vybraný typ ovládacího prvku.|  
  
## <a name="see-also"></a>Viz také  
 [Mapování zpráv do funkcí](../../mfc/reference/mapping-messages-to-functions.md)   
 [Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Přidání třídy](../../ide/adding-a-class-visual-cpp.md)   
 [Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)   
 [Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Přepisování virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Popisovač zpráv knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navigace strukturou třídy](../../ide/navigating-the-class-structure-visual-cpp.md)
