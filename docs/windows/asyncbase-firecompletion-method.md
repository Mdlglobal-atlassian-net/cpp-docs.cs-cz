---
title: Asyncbase::firecompletion – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireCompletion
dev_langs:
- C++
helpviewer_keywords:
- FireCompletion method
ms.assetid: b5e29d6d-52e7-4148-a7f3-a313b1359819
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0cd18d340a11575ed9f6f52d92a5910dcee1faec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859732"
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