---
title: Synclockt::synclockt – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT, constructor
ms.assetid: 713dfd9f-7369-4d86-b4a0-8b32c184d89b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d4ff3393e30e72bc3378837ff11c41927249d1f
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014187"
---
# <a name="synclocktsynclockt-constructor"></a>SyncLockT::SyncLockT – konstruktor
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SyncLockT(  
   _Inout_ SyncLockT&& other  
);  
  
explicit SyncLockT(  
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *Ostatní*  
 Odkaz rvalue na jiný **SyncLockT** objektu.  
  
 *sync*  
 Odkaz na jiný `SyncLockWithStatusT` objektu.  
  
## <a name="remarks"></a>Poznámky  
 Inicializuje novou instanci třídy **SyncLockT** třídy.  
  
 První konstruktor inicializuje aktuální **synclockt –** objektu z jiného **synclockt –** objekt zadaný parametrem *jiných*a pak zruší platnost Další  **Synclockt –** objektu. Druhý konstruktor není **chráněné**a inicializuje aktuální **SyncLockT** objekt má neplatný stav.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [SyncLockT – třída](../windows/synclockt-class.md)