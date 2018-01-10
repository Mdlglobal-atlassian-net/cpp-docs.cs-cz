---
title: "Asyncbase::firecompletion – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::FireCompletion
dev_langs: C++
helpviewer_keywords: FireCompletion method
ms.assetid: b5e29d6d-52e7-4148-a7f3-a313b1359819
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 49716e31148c119d5a8c9eca05b449cea75b405a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasefirecompletion-method"></a>AsyncBase::FireCompletion – metoda
Volá obslužnou rutinu události dokončení nebo obnoví interní průběh delegáta.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void FireCompletion(  
   void  
) override;  
  
virtual void FireCompletion();  
```  
  
## <a name="remarks"></a>Poznámky  
 První verze součásti FireCompletion() obnoví proměnnou interní průběh delegáta. Druhá verze vyvolá obslužné rutiny události dokončení, pokud je dokončení asynchronní operace.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)