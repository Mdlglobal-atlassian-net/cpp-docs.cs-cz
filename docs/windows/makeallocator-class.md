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
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 523bcdb17fc0a1b74fe615e5ff15a6fcef99cc32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
|[MakeAllocator::MakeAllocator – konstruktor](../windows/makeallocator-makeallocator-constructor.md)|Inicializuje novou instanci třídy MakeAllocator.|  
|[MakeAllocator::~MakeAllocator – destruktor](../windows/makeallocator-tilde-makeallocator-destructor.md)|Deinitializes aktuální instance třídy MakeAllocator.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[MakeAllocator::Allocate – metoda](../windows/makeallocator-allocate-method.md)|Přidělí paměť a přidruží ji s aktuálním objektem MakeAllocator.|  
|[MakeAllocator::Detach – metoda](../windows/makeallocator-detach-method.md)|Zrušíte paměti přidělené [přidělte](../windows/makeallocator-allocate-method.md) z aktuálního objektu MakeAllocator metodu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `MakeAllocator`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)