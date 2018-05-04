---
title: Třída CPrimitiveElementTraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bec944c4b9a505cc817dbe7aa3ce09a317954f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cprimitiveelementtraits-class"></a>CPrimitiveElementTraits – třída
Tato třída poskytuje metody výchozí a funkce pro třídu kolekce tvořený primitivní datové typy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>  
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dat se neukládají v objektu třídy kolekce.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání do třídy objektu kolekce elementů.|  
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|Datový typ pro načítání elementy z kolekce třídy objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje výchozí statické funkce a metody pro přesun, kopírování, porovnání a použití algoritmu hash primitivní datové elementy typu uložené v objektu třídy kolekce.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CPrimitiveElementTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="inargtype"></a>  CPrimitiveElementTraits::INARGTYPE  
 Datový typ pro použití při přidávání do třídy objektu kolekce elementů.  
  
```
typedef T INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CPrimitiveElementTraits::OUTARGTYPE  
 Datový typ pro načítání elementy z kolekce třídy objektu.  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Viz také  
 [CDefaultElementTraits – třída](../../atl/reference/cdefaultelementtraits-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
