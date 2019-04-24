---
title: Cdefaultelementtraits – třída
ms.date: 11/04/2016
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
ms.openlocfilehash: 0ee076af5fc4a1c2145162ac510b3a4460e251e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245917"
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

*T*<br/>
Typ dat uložených v kolekci.

## <a name="remarks"></a>Poznámky

Tato třída poskytuje výchozí statické funkce a metody pro přesunutí, kopírování, porovnávání a hash prvků uložených v objektu třídy kolekce. Tato třída odvozená, jeho funkcí a metod od [celementtraitsbase –](../../atl/reference/celementtraitsbase-class.md), [cdefaulthashtraits –](../../atl/reference/cdefaulthashtraits-class.md), a [cdefaultcomparetraits –](../../atl/reference/cdefaultcomparetraits-class.md)a je využíváno [ Celementtraits –](../../atl/reference/celementtraits-class.md), [cprimitiveelementtraits –](../../atl/reference/cprimitiveelementtraits-class.md), a [cheapptrelementtraits –](../../atl/reference/cheapptrelementtraits-class.md).

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
