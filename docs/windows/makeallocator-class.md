---
title: "MakeAllocator – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::MakeAllocator
dev_langs: C++
helpviewer_keywords: MakeAllocator class
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0333dec823cb3996a9546bbfa702b3febf711a61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="makeallocator-class"></a>MakeAllocator – třída
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template<  
   typename T,  
   bool hasWeakReferenceSupport =   
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,   
   T)> , T)> class MakeAllocator;  
  
template<  
   typename T  
>  
class MakeAllocator<T, false>;  
  
template<  
   typename T  
>  
class MakeAllocator<T, true>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Název typu.  
  
 `hasWeakReferenceSupport`  
 `true`přidělení paměti pro objekt, který podporuje slabé odkazy; `false` přidělení paměti pro objekt, který nepodporuje slabé odkazy.  
  
## <a name="remarks"></a>Poznámky  
 Pro třídu activatable s nebo bez podpory slabé odkaz přidělí paměť.  
  
 Přepsání MakeAllocator – třída implementovat model přidělení uživatelské paměti.  
  
 MakeAllocator se obvykle používá, aby se zabránilo nevracení paměti, pokud objekt vyvolá během vytváření.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Makeallocator::makeallocator – konstruktor](../windows/makeallocator-makeallocator-constructor.md)|Inicializuje novou instanci třídy MakeAllocator.|  
|[MakeAllocator:: ~ makeallocator – destruktor](../windows/makeallocator-tilde-makeallocator-destructor.md)|Deinitializes aktuální instance třídy MakeAllocator.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Makeallocator::allocate – metoda](../windows/makeallocator-allocate-method.md)|Přidělí paměť a přidruží ji s aktuálním objektem MakeAllocator.|  
|[Makeallocator::detach – metoda](../windows/makeallocator-detach-method.md)|Zrušíte paměti přidělené [přidělte](../windows/makeallocator-allocate-method.md) z aktuálního objektu MakeAllocator metodu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `MakeAllocator`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)