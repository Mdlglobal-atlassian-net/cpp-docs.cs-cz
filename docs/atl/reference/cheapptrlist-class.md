---
title: Třída CHeapPtrList | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc5b164fda27775a7b3fb272d8718c31815cb1ca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cheapptrlist-class"></a>CHeapPtrList – třída
Tato třída poskytuje metody, které jsou užitečné při sestavování seznamu haldy ukazatele.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename E, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrList 
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```  
  
#### <a name="parameters"></a>Parametry  
 `E`  
 Typ objektu, který má být uložen v třídě kolekce.  
  
 `Allocator`  
 Třída přidělení paměti používat. Výchozí hodnota je [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|Konstruktor|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje konstruktor a je odvozena z metody [CAtlList](../../atl/reference/catllist-class.md) a [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) a usnadňuje vytvoření třídy objektu kolekce ukládání haldy ukazatele.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CHeapPtrList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="cheapptrlist"></a>  CHeapPtrList::CHeapPtrList  
 Konstruktor  
  
```
CHeapPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Velikost bloku.  
  
### <a name="remarks"></a>Poznámky  
 Velikost bloku se rozumí míra množství paměti přidělené, pokud je potřeba nového elementu. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků.  
  
## <a name="see-also"></a>Viz také  
 [CAtlList – třída](../../atl/reference/catllist-class.md)   
 [CHeapPtr – třída](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrElementTraits – třída](../../atl/reference/cheapptrelementtraits-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
