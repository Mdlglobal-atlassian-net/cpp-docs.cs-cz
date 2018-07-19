---
title: Cinterfacelist – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 33cfcc072e000bc903cceb4ac5551071e35610d9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884373"
---
# <a name="cinterfacelist-class"></a>Cinterfacelist – třída
Tato třída poskytuje metody, které jsou užitečné při vytváření seznamu ukazatele rozhraní modelu COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class I, const IID* piid =& __uuidof(I)>  
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceList::CInterfaceList](#cinterfacelist)|Konstruktor pro seznamu rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje konstruktor a odvozené metody pro vytvoření seznamu ukazatele rozhraní modelu COM. Použití [cinterfacearray –](../../atl/reference/cinterfacearray-class.md) když pole je povinné.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Catllist –](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="cinterfacelist"></a>  CInterfaceList::CInterfaceList  
 Konstruktor pro seznamu rozhraní.  
  
```
CInterfaceList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nBlockSize*  
 Velikost bloku, výchozí hodnota je 10.  
  
### <a name="remarks"></a>Poznámky  
 Velikost bloku je míra množství paměti přidělené, pokud je nutné použít nový prvek. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků.  
  
## <a name="see-also"></a>Viz také  
 [Catllist – třída](../../atl/reference/catllist-class.md)   
 [CComQIPtr – třída](../../atl/reference/ccomqiptr-class.md)   
 [Ccomqiptrelementtraits – třída](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
