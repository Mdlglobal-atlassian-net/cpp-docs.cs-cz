---
title: Asyncbase::Start – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Start
dev_langs:
- C++
helpviewer_keywords:
- Start method
ms.assetid: 67405c9d-0d1a-4c1e-8ea4-6ba01c1f90d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32c59c00180b26a2856b1fc210302ffff0e72f0c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641301"
---
# <a name="asyncbasestart-method"></a>AsyncBase::Start – metoda
Spustí asynchronní operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   Start  
)(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK Pokud operaci spuštění nebo je již spuštěna; v opačném případě E_ILLEGAL_STATE_CHANGE.  
  
## <a name="remarks"></a>Poznámky  
 **Start()** je výchozí implementace `IAsyncInfo::Start`, a nemá žádné samotnou práci. Ve skutečnosti spuštění asynchronní operace, přepsat `OnStart()` čistě virtuální metody.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)