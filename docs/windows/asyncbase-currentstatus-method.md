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
ms.openlocfilehash: 36c3f76e3fc137458acddacd834563d845057a24
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646572"
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus – metoda
Načte stav aktuální asynchronní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline void CurrentStatus(  
   Details::AsyncStatusInternal *status  
);  
```  
  
### <a name="parameters"></a>Parametry  
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