---
title: Asyncbase::currentStatus – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CurrentStatus
dev_langs:
- C++
helpviewer_keywords:
- CurrentStatus method
ms.assetid: 26ee4c4a-6525-4a5f-b49c-3ca40c365eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 75b9a07fd88caa9db7f2f145069b0d8857b79fe9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859687"
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus – metoda
Načte stav aktuální asynchronní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline void CurrentStatus(  
   Details::AsyncStatusInternal *status  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `status`  
 Umístění, kde tato operace ukládá aktuální stav.  
  
## <a name="remarks"></a>Poznámky  
 Tato operace je bezpečné pro přístup z více vláken.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)   
 [AsyncStatusInternal – výčet](../windows/asyncstatusinternal-enumeration.md)