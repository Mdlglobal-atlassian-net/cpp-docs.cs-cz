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
ms.openlocfilehash: 45139b16ebb923acd004d995cd9466ea9e39e163
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765733"
---
# <a name="celementtraits-class"></a>Celementtraits – třída

Tato třída používá kolekce tříd poskytují metody a funkce pro přesunutí, kopírování, porovnání a hash operace.

## <a name="syntax"></a>Syntaxe

```
template<typename T>  
class CElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Parametry

`T`  
Typ dat uložených v kolekci.

## <a name="remarks"></a>Poznámky

Tato třída poskytuje výchozí statické funkce a metody pro přesunutí, kopírování, porovnávání a hash prvků uložených v objektu třídy kolekce. `CElementTraits` je zadán jako výchozího zprostředkovatele tyto operace v rámci kolekce tříd [catlarray –](../../atl/reference/catlarray-class.md), [catllist –](../../atl/reference/catllist-class.md), [crbmap –](../../atl/reference/crbmap-class.md), [crbmultimap –](../../atl/reference/crbmultimap-class.md), a [crbtree –](../../atl/reference/crbtree-class.md).

Výchozí implementace, postačí pro jednoduché datové typy, ale pokud třídy kolekce se používají k ukládání více komplexních objektů, funkcí a metod, musí být přepsán uživatelem zadané implementace.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="see-also"></a>Viz také

[Cdefaultelementtraits – třída](../../atl/reference/cdefaultelementtraits-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)
