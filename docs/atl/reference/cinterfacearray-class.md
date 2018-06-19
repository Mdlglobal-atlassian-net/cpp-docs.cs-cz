---
title: Třída CInterfaceArray | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36a24eadea87d0d34adf0f577b321fa16a7cfc86
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359459"
---
# <a name="cinterfacearray-class"></a>CInterfaceArray – třída
Tato třída poskytuje metody, které jsou užitečné při vytváření pole ukazatele rozhraní COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class I, const IID* piid=& __uuidof(I)>  
class CInterfaceArray : 
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>Parametry  
 `I`  
 Určení typu ukazatele k uložení rozhraní modelu COM.  
  
 `piid`  
 Ukazatel na identifikátory IID `I`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Konstruktor pro pole rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje konstruktor a odvozené metody pro vytvoření pole ukazatele rozhraní COM. Použití [CInterfaceList](../../atl/reference/cinterfacelist-class.md) když je požadován jejich seznam.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CAtlArray`  
  
 `CInterfaceArray`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="cinterfacearray"></a>  CInterfaceArray::CInterfaceArray  
 Konstruktor  
  
```
CInterfaceArray() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje pole chytré ukazatele.  
  
## <a name="see-also"></a>Viz také  
 [CAtlArray – třída](../../atl/reference/catlarray-class.md)   
 [Třída CComQIPtr](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits – třída](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
