---
title: SyncLockWithStatusT – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT class
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 51e5a66358890fc20731fb5cb657616484e19db4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890977"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT – třída
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `SyncTraits`  
 Typ, který může trvat exkluzivní nebo sdílené vlastnictví prostředku.  
  
## <a name="remarks"></a>Poznámky  
 Představuje typ, který může trvat exkluzivní nebo sdílené vlastnictví prostředku.  
  
 SyncLockWithStatusT – třída se používá k implementaci [Mutex](../windows/mutex-class1.md) a [Semaphore](../windows/semaphore-class.md) třídy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[SyncLockWithStatusT::SyncLockWithStatusT – konstruktor](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicializuje novou instanci třídy SyncLockWithStatusT.|  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[SyncLockWithStatusT::SyncLockWithStatusT – konstruktor](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicializuje novou instanci třídy SyncLockWithStatusT.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[SyncLockWithStatusT::GetStatus – metoda](../windows/synclockwithstatust-getstatus-method.md)|Načte stav Čekání aktuálního objektu SyncLockWithStatusT.|  
|[SyncLockWithStatusT::IsLocked – metoda](../windows/synclockwithstatust-islocked-method.md)|Určuje, zda je aktuální objekt SyncLockWithStatusT vlastní prostředek; To znamená, je objekt SyncLockWithStatusT *uzamčení*.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[SyncLockWithStatusT::status_ – datový člen](../windows/synclockwithstatust-status-data-member.md)|Blokování výsledek základní čekat po operace uzamčení operaci na objektu založeného na aktuální objekt SyncLockWithStatusT.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `SyncLockT`  
  
 `SyncLockWithStatusT`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers::Details – obor názvů](../windows/microsoft-wrl-wrappers-details-namespace.md)