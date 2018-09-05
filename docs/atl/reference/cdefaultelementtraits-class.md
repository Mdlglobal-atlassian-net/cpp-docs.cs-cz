---
title: Cdefaultelementtraits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de61165ecac24e9c892dd5e95b1bb4e042a34fa1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763780"
---
# <a name="cdefaultelementtraits-class"></a>Cdefaultelementtraits – třída

Tato třída poskytuje výchozí metody a funkce pro třídy kolekce.

## <a name="syntax"></a>Syntaxe

```
template <typename T>  
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```

#### <a name="parameters"></a>Parametry

*T*  
Typ dat uložených v kolekci.

## <a name="remarks"></a>Poznámky

Tato třída poskytuje výchozí statické funkce a metody pro přesunutí, kopírování, porovnávání a hash prvků uložených v objektu třídy kolekce. Tato třída odvozená, jeho funkcí a metod od [celementtraitsbase –](../../atl/reference/celementtraitsbase-class.md), [cdefaulthashtraits –](../../atl/reference/cdefaulthashtraits-class.md), a [cdefaultcomparetraits –](../../atl/reference/cdefaultcomparetraits-class.md)a je využíváno [ Celementtraits –](../../atl/reference/celementtraits-class.md), [cprimitiveelementtraits –](../../atl/reference/cprimitiveelementtraits-class.md), a [cheapptrelementtraits –](../../atl/reference/cheapptrelementtraits-class.md).

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
