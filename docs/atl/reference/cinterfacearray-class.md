---
title: Cinterfacearray – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: c33e0783acfba1b460894ac8f5dde80e61780762
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882710"
---
# <a name="cinterfacearray-class"></a>Cinterfacearray – třída
Tato třída poskytuje metody, které jsou užitečné při vytváření pole z ukazatele rozhraní modelu COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class I, const IID* piid=& __uuidof(I)>  
class CInterfaceArray : 
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>Parametry  
 *I*  
 Rozhraní modelu COM zadání typu ukazatel na Uložit.  
  
 *piid*  
 Ukazatel na IID *můžu*.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Konstruktor pro pole rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje konstruktor a odvozené metody pro vytvoření pole ukazatelů rozhraní modelu COM. Použití [cinterfacelist –](../../atl/reference/cinterfacelist-class.md) při seznam je povinný.  
  
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
 Inicializuje pole inteligentního ukazatele.  
  
## <a name="see-also"></a>Viz také  
 [Catlarray – třída](../../atl/reference/catlarray-class.md)   
 [CComQIPtr – třída](../../atl/reference/ccomqiptr-class.md)   
 [Ccomqiptrelementtraits – třída](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
