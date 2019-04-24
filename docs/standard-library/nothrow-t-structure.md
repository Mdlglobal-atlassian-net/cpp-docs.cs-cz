---
title: nothrow_t – struktura
ms.date: 11/04/2016
f1_keywords:
- nothrow_t
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
ms.openlocfilehash: 2313c436a1fd25149fa7ea72f122a6f323b40028
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223620"
---
# <a name="nothrowt-structure"></a>nothrow_t – struktura

Struktura slouží jako parametr funkce operátoru nové k označení, že funkce by měla vrátit ukazatel s hodnotou null pro sestavy k selhání přidělení, spíše než výjimku.

## <a name="syntax"></a>Syntaxe

```cpp
struct std::nothrow_t {};
```

## <a name="remarks"></a>Poznámky

Struktura pomáhá kompilátoru k výběru správné verze konstruktoru. [nothrow](../standard-library/new-functions.md#nothrow) je synonymum pro objekty typu `std::nothrow_t`.

## <a name="example"></a>Příklad

V tématu [operátor new](../standard-library/new-operators.md#op_new) a [operátor new&#91; &#93; ](../standard-library/new-operators.md#op_new_arr) příklady `std::nothrow_t` se používá jako parametr funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nový >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
