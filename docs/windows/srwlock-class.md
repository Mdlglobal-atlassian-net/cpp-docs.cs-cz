---
title: "Třída SRWLock | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::SRWLock
dev_langs: C++
helpviewer_keywords: SRWLock class
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6721620490a00da0b9c8fa039be0379f4d7dd1b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="srwlock-class"></a>Třída SRWLock
Představuje zámek pro tenký čtečky nebo zápis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class SRWLock;  
```  
  
## <a name="remarks"></a>Poznámky  
 Zámek pro tenký čtečky/zápis se používá k synchronizaci přístup napříč vlákny na objekt nebo prostředků. Další informace najdete v tématu [funkce synchronizace](http://msdn.microsoft.com/en-us/9b6359c2-0113-49b6-83d0-316ad95aba1b).  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|||  
|-|-|  
|**SyncLockExclusive**|Synonymum SRWLock objektu, který je získali ve výhradním režimu.|  
|**SyncLockShared**|Synonymum SRWLock objektu, který je získali ve sdíleném režimu.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Srwlock::srwlock – konstruktor](../windows/srwlock-srwlock-constructor.md)|Inicializuje novou instanci třídy SRWLock.|  
|[SRWLock:: ~ srwlock – destruktor](../windows/srwlock-tilde-srwlock-destructor.md)|Instance třídy SRWLock deinitializes.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Srwlock::lockexclusive – metoda](../windows/srwlock-lockexclusive-method.md)|Získá objekt SRWLock ve výhradním režimu.|  
|[Srwlock::lockshared – metoda](../windows/srwlock-lockshared-method.md)|Získá objekt SRWLock ve sdíleném režimu.|  
|[Srwlock::trylockexclusive – metoda](../windows/srwlock-trylockexclusive-method.md)|Pokusí se získat objekt SRWLock ve výhradním režimu pro objekt SRWLock zadané nebo aktuální.|  
|[Srwlock::trylockshared – metoda](../windows/srwlock-trylockshared-method.md)|Pokusí se získat objekt SRWLock ve sdíleném režimu pro objekt SRWLock zadané nebo aktuální.|  
  
### <a name="protected-data-member"></a>Chráněný datový člen  
  
|Název|Popis|  
|----------|-----------------|  
|[Srwlock::srwlock_ – datový člen](../windows/srwlock-srwlock-data-member.md)|Obsahuje základní proměnná zámek pro aktuální objekt SRWLock.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `SRWLock`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: wrappers – Namespace](../windows/microsoft-wrl-wrappers-namespace.md)