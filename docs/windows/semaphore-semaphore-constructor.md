---
title: Semaphore::Semaphore – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Semaphore, constructor
ms.assetid: 91c22ae7-181e-460d-ad40-70c3a53b26fd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3646e13818297b636a888e1ad00c998a120e8379
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643657"
---
# <a name="semaphoresemaphore-constructor"></a>Semaphore::Semaphore – konstruktor
Inicializuje novou instanci třídy **semafor** třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
explicit Semaphore(  
   HANDLE h  
);  
  
WRL_NOTHROW Semaphore(  
   _Inout_ Semaphore&& h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Popisovač nebo odkaz rvalue na **semafor** objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –
 
 ## <a name="see-also"></a>Viz také
 [Semaphore – třída](../windows/semaphore-class.md)