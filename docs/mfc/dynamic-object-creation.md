---
title: Vytváření dynamických objektů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5763e3f0f3ee5a0e58ac20fe9f637e4f7e097999
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346643"
---
# <a name="dynamic-object-creation"></a>Vytváření dynamických objektů
Tento článek vysvětluje, jak vytvořit objekt dynamicky za běhu. Postup používá run-time třída informace, jak je popsáno v článku [informace o třídě přístup k Run-Time](../mfc/accessing-run-time-class-information.md).  
  
#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>Chcete-li dynamicky vytvořit objekt daný jeho run-time třída  
  
1.  Použít následující kód pro dynamicky vytvoření objektu pomocí `CreateObject` funkce `CRuntimeClass`. Všimněte si, že se při selhání, `CreateObject` vrátí **NULL** místo vyvolání k výjimce:  
  
     [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Použití objektů CObject](../mfc/using-cobject.md)

