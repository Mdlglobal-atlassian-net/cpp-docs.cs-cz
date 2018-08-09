---
title: Semaphore::Operator = – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eee563a52a24d2b78157b640ae6e84217c03af64
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651275"
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator= – operátor
Posune Zadaný popisovač z **semafor** objektů na aktuální **semafor** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Semaphore& operator=(  
   _Inout_ Semaphore&& h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Odkaz rvalue na **semafor** objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Odkaz na aktuální **semafor** objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –
 
 ## <a name="see-also"></a>Viz také
 [Semaphore – třída](../windows/semaphore-class.md)