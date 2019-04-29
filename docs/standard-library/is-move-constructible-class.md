---
title: is_move_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 1b1e450338a123c51b80f40f2369207c8b987cd6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383630"
---
# <a name="ismoveconstructible-class"></a>is_move_constructible – třída

Ověřuje, zda typ má konstruktor move.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, který má být vyhodnocen

## <a name="remarks"></a>Poznámky

Predikát typu, který se vyhodnotí jako true, pokud typ *T* lze sestavit pomocí operace přesunu. Tento predikát je ekvivalentní `is_constructible<T, T&&>`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
