---
title: "Typově bezpečný přístup k ovládacím prvkům bez průvodců kódem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c5a4adce63851620326add61857433b32e1fad5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Typově bezpečný přístup k ovládacím prvkům bez průvodců kódem
Prvním přístupem k vytvoření typově bezpečný přístup k ovládacím prvkům používá funkci člen vložené přetypovat návratový typ třídy `CWnd`na `GetDlgItem` – členská funkce odpovídající typ ovládacího prvku C++, jako v následujícím příkladu:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]  
  
 Potom můžete tuto funkci člen přístup k ovládacím prvku způsobem bezpečnost typů s kódem podobný následujícímu:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Typově bezpečný přístup k ovládacím prvkům v dialogovém okně](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [Typově bezpečný přístup k ovládacím prvkům s průvodci kódem](../mfc/type-safe-access-to-controls-with-code-wizards.md)

