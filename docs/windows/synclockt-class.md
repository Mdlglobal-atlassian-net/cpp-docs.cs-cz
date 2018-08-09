---
title: Synclockt – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT class
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f6b27f45d3a9b9b308a56e1ac8f945969f8c49e2
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643423"
---
# <a name="synclockt-class"></a>SyncLockT – třída
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockT;  
```  
  
### <a name="parameters"></a>Parametry  
 *SyncTraits*  
 Typ, který může převzít vlastnictví prostředku.  
  
## <a name="remarks"></a>Poznámky  
 Představuje typ, který může trvat exkluzivní nebo sdílené vlastnictví prostředku.  
  
 **Synclockt –** třída se používá, třeba k implementaci [SRWLock](../windows/srwlock-class.md) třídy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[SyncLockT::SyncLockT – konstruktor](../windows/synclockt-synclockt-constructor.md)|Inicializuje novou instanci třídy **SyncLockT** třídy.|  
|[SyncLockT::~SyncLockT – destruktor](../windows/synclockt-tilde-synclockt-destructor.md)|Uvolní instanci **SyncLockT** třídy.|  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[SyncLockT::SyncLockT – konstruktor](../windows/synclockt-synclockt-constructor.md)|Inicializuje novou instanci třídy **SyncLockT** třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[SyncLockT::IsLocked – metoda](../windows/synclockt-islocked-method.md)|Označuje, zda aktuální **synclockt –** vlastní prostředek objektu; to znamená, **synclockt –** objekt je *uzamčen*.|  
|[SyncLockT::Unlock – metoda](../windows/synclockt-unlock-method.md)|Verze ovládacího prvku prostředku držené aktuální **SyncLockT** objektu, pokud existuje.|  
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|[SyncLockT::sync_ – datový člen](../windows/synclockt-sync-data-member.md)|Obsahuje základní prostředku reprezentovaného **SyncLockT** třídy.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `SyncLockT`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers::details Namespace](../windows/microsoft-wrl-wrappers-details-namespace.md)   
 [SRWLock – třída](../windows/srwlock-class.md)