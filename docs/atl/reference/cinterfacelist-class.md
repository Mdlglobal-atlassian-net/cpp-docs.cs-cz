---
title: Třída CInterfaceList | Microsoft Docs
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
ms.openlocfilehash: 1fc523b1eccc88678cda48a0c7e429ea0fc09f9b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362171"
---
# <a name="cinterfacelist-class"></a>CInterfaceList – třída
Tato třída poskytuje metody, které jsou užitečné při sestavování seznamu ukazatele rozhraní COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class I, const IID* piid =& __uuidof(I)>  
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceList::CInterfaceList](#cinterfacelist)|V konstruktoru pro seznamu rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje konstruktor a odvozené metody pro vytvoření seznamu ukazatele rozhraní COM. Použití [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) Pokud je požadované pole.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="cinterfacelist"></a>  CInterfaceList::CInterfaceList  
 V konstruktoru pro seznamu rozhraní.  
  
```
CInterfaceList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Velikost bloku, výchozí hodnota je 10.  
  
### <a name="remarks"></a>Poznámky  
 Velikost bloku se rozumí míra množství paměti přidělené, pokud je potřeba nového elementu. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků.  
  
## <a name="see-also"></a>Viz také  
 [CAtlList – třída](../../atl/reference/catllist-class.md)   
 [Třída CComQIPtr](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits – třída](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
