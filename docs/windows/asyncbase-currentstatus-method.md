---
title: Asyncbase::currentStatus – metoda | Dokumentace Microsoftu
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
ms.openlocfilehash: 316dfea16aa129dcaff42424bef46305d2dd56b4
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461426"
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
 *Stav*  
 Umístění, kde tato operace uloží aktuální stav.  
  
## <a name="remarks"></a>Poznámky  
 Tato operace je bezpečná pro vlákno.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Asyncbase – třída](../windows/asyncbase-class.md)   
 [AsyncStatusInternal – výčet](../windows/asyncstatusinternal-enumeration.md)