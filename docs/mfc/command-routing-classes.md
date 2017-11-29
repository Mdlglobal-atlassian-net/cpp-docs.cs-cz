---
title: "Třídy směrování příkazů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.command
dev_langs: C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5e1fb5446a05b8b4227812be77124071abbed2b8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="command-routing-classes"></a>Třídy směrování příkazů
Jako uživatel pracuje s aplikací tak, že zvolíte nabídek nebo ovládací prvek panelu tlačítka myši, aplikace odesílá zprávy z objektu ovlivněných uživatelského rozhraní příslušný příkaz cílový objekt. Příkaz cílové třídy odvozené od `CCmdTarget` zahrnují [CWinApp](../mfc/reference/cwinapp-class.md), [CWnd](../mfc/reference/cwnd-class.md), [CDocTemplate](../mfc/reference/cdoctemplate-class.md), [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), a z nich odvozené třídy. Rozhraní framework podporuje automatické příkaz směrování, aby příkazy mohou být zpracováno nejvhodnější objektem v aplikaci aktuálně aktivní.  
  
 Třída objektu `CCmdUI` předaný cílem příkazu update příkazu uživatelského rozhraní ([on_update_command_ui –](reference/message-map-macros-mfc.md#on_update_command_ui)) obslužné rutiny, která umožňuje aktualizovat stav uživatelského rozhraní pro konkrétní příkaz (za účelem kontroly nebo odeberte Kontrola z položky nabídky). Volání členských funkcí `CCmdUI` objekt, který chcete aktualizovat stav objektu uživatelského rozhraní. Tento proces je stejný, zda je objekt uživatelského rozhraní související s konkrétní příkaz položku nabídky nebo tlačítko nebo obojí.  
  
 [CCmdTarget](../mfc/reference/ccmdtarget-class.md)  
 Slouží jako základní třída pro všechny třídy objektů, které může přijímat a reagovat na zprávy.  
  
 [CCmdUI](../mfc/reference/ccmdui-class.md)  
 Poskytuje programovací rozhraní pro aktualizace objektů uživatelského rozhraní, například položky nabídky nebo ovládací prvek panelu tlačítek. Cílový objekt příkaz povolí, zakáže, kontroluje nebo vymaže objekt uživatelského rozhraní s tímto objektem.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)
