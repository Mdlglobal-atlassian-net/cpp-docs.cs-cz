---
title: CCmdUI – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a857d1cddcc78c7cfff4243b9c99194986af3d9b
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956483"
---
# <a name="the-ccmdui-class"></a>CCmdUI – třída
Když směruje příkazy aktualizace k její obslužnou rutinu, rozhraní předá obslužná rutina ukazatel na `CCmdUI` objektu (nebo na objekt `CCmdUI`-odvozené třídy). Tento objekt představuje nabídky položky nebo panelu nástrojů tlačítko nebo jiného objektu uživatelského rozhraní, který vygeneroval příkaz. Obslužná rutina aktualizace volání členských funkcí `CCmdUI` struktura prostřednictvím má ukazatel na aktualizace objektů uživatelského rozhraní. Zde je ukázka, obslužnou rutinu aktualizace pro položku nabídky Vymazat vše:  
  
 [!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]  
  
 Tuto obslužnou rutinu volání `Enable` – členská funkce objektu s přístupem k položce nabídky. `Enable` Položka se k dispozici pro použití.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)

