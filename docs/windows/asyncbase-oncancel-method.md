---
title: "Asyncbase::oncancel – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::OnCancel
dev_langs:
- C++
helpviewer_keywords:
- OnCancel method
ms.assetid: 4bd0b68e-a9df-4913-9f6c-e093ed55c3f9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6dd20f90fa1ead9504a223dab2fe38f3bace0c3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbaseoncancel-method"></a>AsyncBase::OnCancel – metoda
Při přepisu v odvozené třídě, zruší asynchronní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
virtual void OnCancel(  
   void  
) = 0;  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)   
 [AsyncBase::Cancel – metoda](../windows/asyncbase-cancel-method.md)