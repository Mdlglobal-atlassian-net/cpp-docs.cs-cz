---
title: Třída CAutoVectorPtrElementTraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 52c450a1a261224cf87ea125a6f01259da0e9f1b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357880"
---
# <a name="cautovectorptrelementtraits-class"></a>CAutoVectorPtrElementTraits – třída
Tato třída poskytuje metody, statické funkce a definice TypeDef užitečné při vytváření kolekcí chytré ukazatele pomocí vektoru nové a odstranit operátory.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>  
class CAutoVectorPtrElementTraits : 
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```    
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ ukazatele.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání do třídy objektu kolekce elementů.|  
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|Datový typ pro načítání elementy z kolekce třídy objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje metody, statické funkce a definice TypeDef pro pomoc vytvoření objektů tříd kolekce obsahující chytré ukazatele. Na rozdíl od [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md), tato třída používá nové vector a odstranit operátory.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoVectorPtrElementTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="inargtype"></a>  CAutoVectorPtrElementTraits::INARGTYPE  
 Datový typ pro použití při přidávání do třídy objektu kolekce elementů.  
  
```
typedef CAutoVectorPtr<T>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CAutoVectorPtrElementTraits::OUTARGTYPE  
 Datový typ pro načítání elementy z kolekce třídy objektu.  
  
```
typedef T*& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Viz také  
 [CDefaultElementTraits – třída](../../atl/reference/cdefaultelementtraits-class.md)   
 [CAutoVectorPtr – třída](../../atl/reference/cautovectorptr-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
