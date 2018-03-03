---
title: "CCmdUI – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CCmdUI
dev_langs:
- C++
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efb87fc04ee9ee55806ec4fc1103ded42231b433
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="the-ccmdui-class"></a>CCmdUI – třída
Když směruje příkazy aktualizace k její obslužnou rutinu, rozhraní předá obslužná rutina ukazatel na `CCmdUI` objektu (nebo na objekt `CCmdUI`-odvozené třídy). Tento objekt představuje nabídky položky nebo panelu nástrojů tlačítko nebo jiného objektu uživatelského rozhraní, který vygeneroval příkaz. Obslužná rutina aktualizace volání členských funkcí `CCmdUI` struktura prostřednictvím má ukazatel na aktualizace objektů uživatelského rozhraní. Zde je ukázka, obslužnou rutinu aktualizace pro položku nabídky Vymazat vše:  
  
 [!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]  
  
 Tuto obslužnou rutinu volání **povolit** – členská funkce objektu s přístupem k položce nabídky. **Povolit** zpřístupní položku pro použití.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)

