---
title: "Třída CElementTraits | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
dev_langs: C++
helpviewer_keywords: CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cda18f6148f9a1cbc39a6e7003cce6324e36eeeb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 Tato třída poskytuje výchozí statické funkce a metody pro přesun, kopírování, porovnání a hash elementy, které jsou uložené v objektu třídy kolekce. `CElementTraits`je zadána jako výchozí zprostředkovatel z těchto operací třídy kolekce [CAtlArray](../../atl/reference/catlarray-class.md), [CAtlList](../../atl/reference/catllist-class.md), [CRBMap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md), a [CRBTree](../../atl/reference/crbtree-class.md).  
  
 Výchozí implementace postačí pro jednoduché datové typy, ale pokud třídy kolekce se používají k ukládání objektů složitější, funkce a metody musí být přepsána implementacemi zadanou uživatelem.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
## <a name="see-also"></a>Viz také  
 [CDefaultElementTraits – třída](../../atl/reference/cdefaultelementtraits-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)