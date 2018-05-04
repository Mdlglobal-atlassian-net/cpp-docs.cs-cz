---
title: Třída CAutoPtrElementTraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c845243e3b99be10af70042688e672fa867fb888
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cautoptrelementtraits-class"></a>CAutoPtrElementTraits – třída
Tato třída poskytuje metody, statické funkce a definice TypeDef užitečné při vytváření kolekcí chytré ukazatele.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T>  
class CAutoPtrElementTraits 
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```    
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ ukazatele.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání do třídy objektu kolekce elementů.|  
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|Datový typ pro načítání elementy z kolekce třídy objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje metody, statické funkce a definice TypeDef pro pomoc vytvoření objektů tříd kolekce obsahující chytré ukazatele. Třídy [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) a [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) odvozena od `CAutoPtrElementTraits`. Pokud vytváření kolekce chytré ukazatele, který vyžaduje vektor – nový a odstranění operátory, použijte [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) místo.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoPtrElementTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="inargtype"></a>  CAutoPtrElementTraits::INARGTYPE  
 Datový typ pro použití při přidávání do třídy objektu kolekce elementů.  
  
```
typedef CAutoPtr<T>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CAutoPtrElementTraits::OUTARGTYPE  
 Datový typ pro načítání elementy z kolekce třídy objektu.  
  
```
typedef T *& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Viz také  
 [CDefaultElementTraits – třída](../../atl/reference/cdefaultelementtraits-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
