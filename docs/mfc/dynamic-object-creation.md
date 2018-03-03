---
title: "Vytváření dynamických objektů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 755cbf614966ad6faedbe8db9bbf11ac88c63328
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dynamic-object-creation"></a>Vytváření dynamických objektů
Tento článek vysvětluje, jak vytvořit objekt dynamicky za běhu. Postup používá run-time třída informace, jak je popsáno v článku [informace o třídě přístup k Run-Time](../mfc/accessing-run-time-class-information.md).  
  
#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>Chcete-li dynamicky vytvořit objekt daný jeho run-time třída  
  
1.  Použít následující kód pro dynamicky vytvoření objektu pomocí `CreateObject` funkce `CRuntimeClass`. Všimněte si, že se při selhání, `CreateObject` vrátí **NULL** místo vyvolání k výjimce:  
  
     [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Použití objektů CObject](../mfc/using-cobject.md)

