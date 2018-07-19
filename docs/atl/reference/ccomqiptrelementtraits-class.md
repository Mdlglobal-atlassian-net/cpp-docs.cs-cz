---
title: Ccomqiptrelementtraits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e99299d1232fda75d6b0552b5236a060903a08e5
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879649"
---
# <a name="ccomqiptrelementtraits-class"></a>Ccomqiptrelementtraits – třída
Tato třída poskytuje metody, statické funkce a definice TypeDef, které jsou užitečné při vytváření kolekce ukazatele rozhraní modelu COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename I, const IID* piid=& __uuidof(I)>  
class CComQIPtrElementTraits : 
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```  
  
#### <a name="parameters"></a>Parametry  
 *I*  
 Rozhraní modelu COM zadání typu ukazatel na Uložit.  
  
 *piid*  
 Ukazatel na IID *můžu*.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání prvků do objektu třídy kolekce.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída je odvozena metody a obsahuje definice typu poskytující užitečné při vytváření třídy kolekce z [CComQIPtr](../../atl/reference/ccomqiptr-class.md) objektů ukazatele rozhraní modelu COM. Tato třída se používá i [cinterfacearray –](../../atl/reference/cinterfacearray-class.md) a [cinterfacelist –](../../atl/reference/cinterfacelist-class.md) třídy.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Cdefaultcomparetraits –](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [Cdefaulthashtraits –](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [Celementtraitsbase –](../../atl/reference/celementtraitsbase-class.md)  
  
 [Cdefaultelementtraits –](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CComQIPtrElementTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="inargtype"></a>  CComQIPtrElementTraits::INARGTYPE  
 Datový typ pro použití při přidávání prvků do objektu třídy kolekce.  
  
```
typedef I* INARGTYPE;
```  
  
## <a name="see-also"></a>Viz také  
 [Cdefaultelementtraits – třída](../../atl/reference/cdefaultelementtraits-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
