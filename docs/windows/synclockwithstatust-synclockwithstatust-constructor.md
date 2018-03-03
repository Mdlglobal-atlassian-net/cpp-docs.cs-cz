---
title: "Synclockwithstatust::synclockwithstatust – konstruktor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc5be4a37182cb23b47a2511d2e7d5eb0ffa558a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT – konstruktor
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLockWithStatusT(  
   _Inout_ SyncLockWithStatusT&& other  
);  
  
explicit SyncLockWithStatusT(  
   typename SyncTraits::Type sync,  
   DWORD status  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `other`  
 Rvalue – odkaz na jiný objekt SyncLockWithStatusT.  
  
 `sync`  
 Odkaz na jiný objekt SyncLockWithStatusT.  
  
 `status`  
 Hodnota [status_ –](../windows/synclockwithstatust-status-data-member.md) členem data `other` parametr nebo `sync` parametr.  
  
## <a name="remarks"></a>Poznámky  
 Inicializuje novou instanci třídy SyncLockWithStatusT.  
  
 První konstruktor inicializuje aktuální objekt SyncLockWithStatusT z jiné SyncLockWithStatusT určený parametrem `other`a pak zruší platnost druhý SyncLockWithStatusT objekt. Druhý konstruktor je `protected`a inicializuje aktuální SyncLockWithStatusT objekt, který má neplatný stav.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [SyncLockWithStatusT – třída](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus – metoda](../windows/synclockwithstatust-getstatus-method.md)