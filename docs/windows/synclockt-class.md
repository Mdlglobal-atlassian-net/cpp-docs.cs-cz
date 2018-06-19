---
title: SyncLockT – třída | Microsoft Docs
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
ms.openlocfilehash: e05a1be5d84db52573d3c3235936ecf82dde5894
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892849"
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