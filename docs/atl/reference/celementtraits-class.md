---
title: Celementtraits – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 61cbd301d01d62c0d24f232703b53cebf411a082
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021067"
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

## <a name="see-also"></a>Viz také

[CDefaultElementTraits – třída](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
