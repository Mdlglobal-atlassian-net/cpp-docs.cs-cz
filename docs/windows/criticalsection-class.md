---
title: "CriticalSection – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::CriticalSection
dev_langs: C++
helpviewer_keywords: CriticalSection class
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e2bf6e4728bac6622f9872ab939e084b14f49ae8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsection-class"></a>CriticalSection – třída
Představuje objekt kritická sekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CriticalSection;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="constructor"></a>Konstruktor  
  
|Název|Popis|  
|----------|-----------------|  
|[CriticalSection::CriticalSection – konstruktor](../windows/criticalsection-criticalsection-constructor.md)|Inicializuje objekt synchronizace, který je podobný objekt mutex, ale mohou být využívána pouze vláken v jednom procesu.|  
|[CriticalSection::~CriticalSection – destruktor](../windows/criticalsection-tilde-criticalsection-destructor.md)|Deinitializes a zničí aktuální objekt CriticalSection.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CriticalSection::TryLock – metoda](../windows/criticalsection-trylock-method.md)|Pokusy o zadání kritická sekce bez blokování. Pokud je volání úspěšné, volající vlákno převezme vlastnictví kritická sekce.|  
|[CriticalSection::Lock – metoda](../windows/criticalsection-lock-method.md)|Čeká na vlastnictví objektu zadaného kritická sekce. Funkce vrátí hodnotu, pokud volající vlákno je uděleno vlastnictví.|  
|[CriticalSection::IsValid – metoda](../windows/criticalsection-isvalid-method.md)|Určuje, zda je aktuální kritická sekce platný.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CriticalSection::cs_ – datový člen](../windows/criticalsection-cs-data-member.md)|Deklaruje člena kritická sekce.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CriticalSection`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)