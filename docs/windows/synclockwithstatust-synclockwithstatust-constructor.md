---
title: Synclockwithstatust::synclockwithstatust – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 21ce2054cabf257594cb3fa376236b9a1e504a59
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647752"
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT – konstruktor
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
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
  
### <a name="parameters"></a>Parametry  
 *Ostatní*  
 Odkaz rvalue na jiný **synclockwithstatust –** objektu.  
  
 *sync*  
 Odkaz na jiný **synclockwithstatust –** objektu.  
  
 *Stav*  
 Hodnota [status_ –](../windows/synclockwithstatust-status-data-member.md) datový člen třídy *jiných* parametr nebo *synchronizace* parametr.  
  
## <a name="remarks"></a>Poznámky  
 Inicializuje novou instanci třídy **synclockwithstatust –** třídy.  
  
 První konstruktor inicializuje aktuální **synclockwithstatust –** objektu z jiného **synclockwithstatust –** určené parametrem *jiných*a pak zruší platnost druhé **synclockwithstatust –** objektu. Druhý konstruktor není **chráněné**a inicializuje aktuální **synclockwithstatust –** objekt má neplatný stav.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [Synclockwithstatust – třída](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus – metoda](../windows/synclockwithstatust-getstatus-method.md)