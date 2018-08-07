---
title: Makeallocator – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- MakeAllocator class
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c87f1191bc90cd2aec9207f3a4657349c9859bf4
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605916"
---
# <a name="makeallocator-class"></a>MakeAllocator – třída
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename T,  
   bool hasWeakReferenceSupport =   
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>, T)>
 class MakeAllocator;  
  
template<typename T>  
class MakeAllocator<T, false>;  
  
template<typename T>  
class MakeAllocator<T, true>;  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Název typu.  
  
 *hasWeakReferenceSupport*  
 **Hodnota TRUE** přidělení paměti pro objekt, který podporuje slabé odkazy; **false** přidělení paměti pro objekt, který nepodporuje slabé odkazy.  
  
## <a name="remarks"></a>Poznámky  
 Přiděluje paměť pro aktivovatelné třídy s nebo bez něj slabou podporu odkazu.  
  
 Přepsat **MakeAllocator** třídu pro implementaci modelu přidělování paměti definované uživatelem.  
  
 **Makeallocator –** se obvykle používá pro zabránění nevracení paměti, pokud objekt vyvolá během konstrukce.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[MakeAllocator::MakeAllocator – konstruktor](../windows/makeallocator-makeallocator-constructor.md)|Inicializuje novou instanci třídy **MakeAllocator** třídy.|  
|[MakeAllocator::~MakeAllocator – destruktor](../windows/makeallocator-tilde-makeallocator-destructor.md)|Zruší inicializaci aktuální instance **MakeAllocator** třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[MakeAllocator::Allocate – metoda](../windows/makeallocator-allocate-method.md)|Přidělí paměť a přidruží ji k aktuální **MakeAllocator** objektu.|  
|[MakeAllocator::Detach – metoda](../windows/makeallocator-detach-method.md)|Zruší přidružení paměť přidělenou [přidělení](../windows/makeallocator-allocate-method.md) metodu z aktuální **MakeAllocator** objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `MakeAllocator`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)