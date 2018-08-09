---
title: Semafor třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Semaphore class
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5101aba24cd8a0ed4f44587ffc4ad9e973099b8a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652633"
---
# <a name="semaphore-class"></a>Semaphore – třída
Představuje objekt synchronizace, který řídí sdíleného prostředku, který podporuje omezený počet uživatelů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`SyncLock`|Synonymum pro třídu, která podporuje synchronní zámky.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Semaphore::Semaphore – konstruktor](../windows/semaphore-semaphore-constructor.md)|Inicializuje novou instanci třídy **semafor** třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[InvokeHelper::Invoke – metoda](../windows/invokehelper-invoke-method.md)|Volá obslužnou rutinu události, jehož předpis obsahuje zadaný počet argumentů.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Semaphore::Lock – metoda](../windows/semaphore-lock-method.md)|Počká, dokud aktuální objekt nebo objekt přidružený k zadanému popisovači, je do signalizovaného stavu nebo zadaný časový limit uplynul.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Semaphore::operator= – operátor](../windows/semaphore-operator-assign-operator.md)|Posune Zadaný popisovač z **semafor** objektů na aktuální **semafor** objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Semaphore`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)