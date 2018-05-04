---
title: Třída CElementTraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c530622f096ef14d4eb3de56e5219e8f7df4f082
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="celementtraits-class"></a>CElementTraits – třída
Tato třída je používá k zajištění metody a funkce pro přesunutí, kopírování, porovnání a hash operace třídy kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T>  
class CElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dat se neukládají v kolekci.  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje výchozí statické funkce a metody pro přesun, kopírování, porovnání a hash elementy, které jsou uložené v objektu třídy kolekce. `CElementTraits` je zadána jako výchozí zprostředkovatel z těchto operací třídy kolekce [CAtlArray](../../atl/reference/catlarray-class.md), [CAtlList](../../atl/reference/catllist-class.md), [CRBMap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md), a [CRBTree](../../atl/reference/crbtree-class.md).  
  
 Výchozí implementace postačí pro jednoduché datové typy, ale pokud třídy kolekce se používají k ukládání objektů složitější, funkce a metody musí být přepsána implementacemi zadanou uživatelem.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
## <a name="see-also"></a>Viz také  
 [CDefaultElementTraits – třída](../../atl/reference/cdefaultelementtraits-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
