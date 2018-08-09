---
title: Asyncbase::fireprogress – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireProgress
dev_langs:
- C++
helpviewer_keywords:
- FireProgress method
ms.assetid: 4512bef6-0ebc-4465-9b8a-4c9dfa82084c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 35faad82357b0f449d407787840c865b798427f1
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642006"
---
# <a name="asyncbasefireprogress-method"></a>AsyncBase::FireProgress – metoda
Vyvolá obslužnou rutinu události aktuální průběh.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void FireProgress(  
   const typename ProgressTraits::Arg2Type arg  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *arg*  
 Metoda obslužné rutiny události, která se má vyvolat.  
  
## <a name="remarks"></a>Poznámky  
 `ProgressTraits` je odvozen z [argtraitshelper – struktura](../windows/argtraitshelper-structure.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)