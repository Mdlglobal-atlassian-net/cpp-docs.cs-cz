---
title: Celementtraits – třída
ms.date: 11/04/2016
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
helpviewer_keywords:
- CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
ms.openlocfilehash: 646b445aed93c9041932c60442f61792f5e1a7e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245765"
---
# <a name="celementtraits-class"></a>Celementtraits – třída

Tato třída používá kolekce tříd poskytují metody a funkce pro přesunutí, kopírování, porovnání a hash operace.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat uložených v kolekci.

## <a name="remarks"></a>Poznámky

Tato třída poskytuje výchozí statické funkce a metody pro přesunutí, kopírování, porovnávání a hash prvků uložených v objektu třídy kolekce. `CElementTraits` je zadán jako výchozího zprostředkovatele tyto operace v rámci kolekce tříd [catlarray –](../../atl/reference/catlarray-class.md), [catllist –](../../atl/reference/catllist-class.md), [crbmap –](../../atl/reference/crbmap-class.md), [crbmultimap –](../../atl/reference/crbmultimap-class.md), a [crbtree –](../../atl/reference/crbtree-class.md).

Výchozí implementace, postačí pro jednoduché datové typy, ale pokud třídy kolekce se používají k ukládání více komplexních objektů, funkcí a metod, musí být přepsán uživatelem zadané implementace.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="see-also"></a>Viz také:

[CDefaultElementTraits – třída](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
