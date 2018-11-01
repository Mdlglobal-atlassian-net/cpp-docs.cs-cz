---
title: Cdefaultelementtraits – třída
ms.date: 11/04/2016
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
ms.openlocfilehash: 2cf93adc5b78a8fa31a603d58f0e4dbe1efb0d6d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494685"
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

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
