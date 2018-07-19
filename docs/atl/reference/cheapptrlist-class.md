---
title: Cheapptrlist – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: cd3342e7c64a13761830073cd3ed82b627b8c407
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879293"
---
# <a name="cheapptrlist-class"></a>Cheapptrlist – třída
Tato třída poskytuje metody, které jsou užitečné při vytváření seznamu haldy ukazatele.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename E, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrList 
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```  
  
#### <a name="parameters"></a>Parametry  
 *E*  
 Typ objektu ukládaly ve třídě kolekce.  
  
 *Allocator –*  
 Třída přidělení paměti pro použití. Výchozí hodnota je [ccrtallocator –](../../atl/reference/ccrtallocator-class.md).  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|Konstruktor|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje konstruktor a je odvozena z metody [catllist –](../../atl/reference/catllist-class.md) a [cheapptrelementtraits –](../../atl/reference/cheapptrelementtraits-class.md) pro vytvoření objektu třídy kolekce ukládání ukazatelů haldy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Catllist –](../../atl/reference/catllist-class.md)  
  
 `CHeapPtrList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="cheapptrlist"></a>  CHeapPtrList::CHeapPtrList  
 Konstruktor  
  
```
CHeapPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nBlockSize*  
 Velikost bloku.  
  
### <a name="remarks"></a>Poznámky  
 Velikost bloku je míra množství paměti přidělené, pokud je nutné použít nový prvek. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků.  
  
## <a name="see-also"></a>Viz také  
 [Catllist – třída](../../atl/reference/catllist-class.md)   
 [Cheapptr – třída](../../atl/reference/cheapptr-class.md)   
 [Cheapptrelementtraits – třída](../../atl/reference/cheapptrelementtraits-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
