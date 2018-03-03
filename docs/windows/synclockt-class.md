---
title: "SyncLockT – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT class
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f3a9794f7b00a2029f6706db3a846ba127a4d5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="synclockt-class"></a>SyncLockT – třída
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockT;  
```  
  
#### <a name="parameters"></a>Parametry  
 `SyncTraits`  
 Typ, který může převzít vlastnictví prostředku.  
  
## <a name="remarks"></a>Poznámky  
 Představuje typ, který může trvat exkluzivní nebo sdílené vlastnictví prostředku.  
  
 SyncLockT – třída slouží, například při provádění [SRWLock](../windows/srwlock-class.md) třídy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[SyncLockT::SyncLockT – konstruktor](../windows/synclockt-synclockt-constructor.md)|Inicializuje novou instanci třídy SyncLockT – třída.|  
|[SyncLockT::~SyncLockT – destruktor](../windows/synclockt-tilde-synclockt-destructor.md)|Instance třídy SyncLockT deinitializes.|  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[SyncLockT::SyncLockT – konstruktor](../windows/synclockt-synclockt-constructor.md)|Inicializuje novou instanci třídy SyncLockT – třída.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[SyncLockT::IsLocked – metoda](../windows/synclockt-islocked-method.md)|Určuje, zda je aktuální objekt SyncLockT vlastní prostředek; To znamená, je objekt SyncLockT *uzamčení*.|  
|[SyncLockT::Unlock – metoda](../windows/synclockt-unlock-method.md)|Uvolní ovládacího prvku prostředku uchovávat aktuální objekt SyncLockT, pokud existuje.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[SyncLockT::sync_ – datový člen](../windows/synclockt-sync-data-member.md)|Obsahuje základní prostředku reprezentovaného parametrem SyncLockT – třída.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `SyncLockT`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [Namespace Microsoft::WRL::Wrappers::details](../windows/microsoft-wrl-wrappers-details-namespace.md)   
 [SRWLock – třída](../windows/srwlock-class.md)