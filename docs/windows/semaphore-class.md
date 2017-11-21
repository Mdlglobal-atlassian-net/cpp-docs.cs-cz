---
title: "Semafor třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Semaphore
dev_langs: C++
helpviewer_keywords: Semaphore class
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 10de04ebed31835d93daca9cf4caa5d96ed605b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="semaphore-class"></a>Semaphore – třída
Představuje objekt synchronizace, který řídí sdílený prostředek, který podporuje omezený počet uživatelů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`SyncLock`|Synonymum pro třídu, která podporuje synchronní zámky.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Semaphore::Semaphore – konstruktor](../windows/semaphore-semaphore-constructor.md)|Inicializuje novou instanci třídy semafor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Invokehelper::Invoke – metoda](../windows/invokehelper-invoke-method.md)|Volá obslužnou rutinu události, jejichž podpis obsahuje zadaný počet argumentů.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Semaphore::Lock – metoda](../windows/semaphore-lock-method.md)|Počká, dokud nebude aktuální objekt nebo objekt přidružený k zadanému popisovači, je ve stavu signalizovaného nebo zadaný časový limit uplynul.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Semaphore::Operator = – operátor](../windows/semaphore-operator-assign-operator.md)|Přesune zadaný popisovač z objektu semaforu pro aktuální objekt semafor.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Semaphore`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: wrappers – Namespace](../windows/microsoft-wrl-wrappers-namespace.md)