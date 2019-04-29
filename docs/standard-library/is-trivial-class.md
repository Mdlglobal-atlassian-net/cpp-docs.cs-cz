---
title: is_trivial – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivial
helpviewer_keywords:
- is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
ms.openlocfilehash: 609fdd9c3d0d00eea607db4aefd31163234a9a00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413512"
---
# <a name="istrivial-class"></a>is_trivial – třída

Ověřuje, zda typ je typ jednoduchého dotazu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivial;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* triviální typ, jinak má hodnotu false. Triviální typy jsou Skalární typy, typy triviálně kopírovatelné tříd, polí těchto typů a verzích kvalifikovaných cv tyto typy.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
