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
ms.openlocfilehash: 89587f87bd71d2688bba2c128d28c01212b50b71
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|[Criticalsection::criticalsection – konstruktor](../windows/criticalsection-criticalsection-constructor.md)|Inicializuje objekt synchronizace, který je podobný objekt mutex, ale mohou být využívána pouze vláken v jednom procesu.|  
|[CriticalSection:: ~ criticalsection – destruktor](../windows/criticalsection-tilde-criticalsection-destructor.md)|Deinitializes a zničí aktuální objekt CriticalSection.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Criticalsection::trylock – metoda](../windows/criticalsection-trylock-method.md)|Pokusy o zadání kritická sekce bez blokování. Pokud je volání úspěšné, volající vlákno převezme vlastnictví kritická sekce.|  
|[Criticalsection::Lock – metoda](../windows/criticalsection-lock-method.md)|Čeká na vlastnictví objektu zadaného kritická sekce. Funkce vrátí hodnotu, pokud volající vlákno je uděleno vlastnictví.|  
|[Criticalsection::IsValid – metoda](../windows/criticalsection-isvalid-method.md)|Určuje, zda je aktuální kritická sekce platný.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Criticalsection::cs_ – datový člen](../windows/criticalsection-cs-data-member.md)|Deklaruje člena kritická sekce.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CriticalSection`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: wrappers – Namespace](../windows/microsoft-wrl-wrappers-namespace.md)