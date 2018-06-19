---
title: Třída CAutoPtrList | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9101d66de6782d1a060a8acdfb0d02e9971bb9c5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357542"
---
# <a name="cautoptrlist-class"></a>CAutoPtrList – třída
Tato třída poskytuje metody, které jsou užitečné při sestavování seznamu chytré ukazatele.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename E>  
class CAutoPtrList : 
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>Parametry  
 `E`  
 Typ ukazatele.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|Konstruktor|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje konstruktor a je odvozena z metody [CAtlList](../../atl/reference/catllist-class.md) a [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) a usnadňuje vytvoření objektu seznamu ukládání chytré ukazatele. Třída [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) poskytuje podobné funkce pro objekt array.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CAutoPtrList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="cautoptrlist"></a>  CAutoPtrList::CAutoPtrList  
 Konstruktor  
  
```
CAutoPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Velikost bloku, výchozí hodnota je 10.  
  
### <a name="remarks"></a>Poznámky  
 Velikost bloku se rozumí míra množství paměti přidělené, pokud je potřeba nového elementu. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků.  
  
## <a name="see-also"></a>Viz také  
 [CAtlList – třída](../../atl/reference/catllist-class.md)   
 [CAutoPtrElementTraits – třída](../../atl/reference/cautoptrelementtraits-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
