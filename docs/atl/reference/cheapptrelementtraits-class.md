---
title: Cheapptrelementtraits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1aa3921f79e8c368fe4a42c3b56ede27f436e25
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884097"
---
# <a name="cheapptrelementtraits-class"></a>Cheapptrelementtraits – třída
Tato třída poskytuje metody, statické funkce a definice TypeDef, které jsou užitečné při vytváření kolekce haldy ukazatelů.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrElementTraits : 
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Typ objektu ukládaly ve třídě kolekce.  
  
 *Allocator –*  
 Třída přidělení paměti pro použití. Výchozí hodnota je [ccrtallocator –](../../atl/reference/ccrtallocator-class.md).  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání prvků do objektu třídy kolekce.|  
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|Datový typ použitý pro získání prvky z třídy objektu kolekce.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje metody, statické funkce a funkce TypeDef pro pomoc zřízení objekty třídy kolekcí obsahujících ukazatele haldy. Třída `CHeapPtrList` je odvozena z `CHeapPtrElementTraits`.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Cdefaultcomparetraits –](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [Cdefaulthashtraits –](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [Celementtraitsbase –](../../atl/reference/celementtraitsbase-class.md)  
  
 [Cdefaultelementtraits –](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CHeapPtrElementTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="inargtype"></a>  CHeapPtrElementTraits::INARGTYPE  
 Datový typ pro použití při přidávání prvků do objektu třídy kolekce.  
  
```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CHeapPtrElementTraits::OUTARGTYPE  
 Datový typ použitý pro získání prvky z třídy objektu kolekce.  
  
```
typedef T *& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Viz také  
 [Cdefaultelementtraits – třída](../../atl/reference/cdefaultelementtraits-class.md)   
 [Ccomheapptr – třída](../../atl/reference/ccomheapptr-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
