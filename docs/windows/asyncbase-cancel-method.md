---
title: Asyncbase::Cancel – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Cancel
dev_langs:
- C++
helpviewer_keywords:
- Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 439a118bbea5adce4c306298e573bed85da26291
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641901"
---
# <a name="asyncbasecancel-method"></a>AsyncBase::Cancel – metoda
Zruší asynchronní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   Cancel  
)(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ve výchozím nastavení vždy vrátí hodnotu S_OK.  
  
## <a name="remarks"></a>Poznámky  
 **Cancel()** je výchozí implementace `IAsyncInfo::Cancel`, a nemá žádné samotnou práci. Pokud chcete skutečně zrušit asynchronní operaci, přepsat `OnCancel()` čistě virtuální metody.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)