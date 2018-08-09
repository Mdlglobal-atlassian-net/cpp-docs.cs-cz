---
title: Synclockt::islocked – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: a81fea43-f99a-4708-812a-7fd6af500d3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4609866b25f574f34b620d81de3a21d6b608db6
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020316"
---
# <a name="synclocktislocked-method"></a>SyncLockT::IsLocked – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
bool IsLocked() const;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** Pokud **synclockt –** objekt je uzamčena, jinak **false**.  
  
## <a name="remarks"></a>Poznámky  
 Označuje, zda aktuální **synclockt –** vlastní prostředek objektu; to znamená, **synclockt –** objekt je *uzamčen*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [SyncLockT – třída](../windows/synclockt-class.md)