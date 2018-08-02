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
ms.openlocfilehash: ab47405f81cf6fb92af215f1868d8ad7c42bffa7
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463727"
---
# <a name="asyncbasestart-method"></a>AsyncBase::Start – metoda
Spustí asynchronní operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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