---
title: make_signed – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_signed
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
ms.openlocfilehash: c9fe9d54d503f1aa1dfb3debfaeb7649f2e5c18d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631644"
---
# <a name="makesigned-class"></a>make_signed – třída

Vytvoří typ nebo nejmenší znaménkem typu větší než nebo rovno velikosti typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct make_signed;

template <class T>
using make_signed_t = typename make_signed<T>::type;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Instance modifikátoru typu obsahuje změněný typ, který je *T* Pokud `is_signed<T>` platí. V opačném případě je nejmenší typ bez znaménka `UT` pro kterou `sizeof (T) <= sizeof (UT)`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
