---
title: make_unsigned – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_unsigned
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
ms.openlocfilehash: 42c722c5250a4989b930d8f1e6fe52f2eccc614a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439647"
---
# <a name="makeunsigned-class"></a>make_unsigned – třída

Vytvoří typ nebo nejmenší bez znaménka typu větší než nebo rovno velikosti typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*T*|Typ, který chcete upravit.|

## <a name="remarks"></a>Poznámky

Instance modifikátoru typu obsahuje změněný typ, který je *T* Pokud `is_unsigned<T>` platí. V opačném případě je nejmenší typ se znaménkem `ST` pro kterou `sizeof (T) <= sizeof (ST)`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
