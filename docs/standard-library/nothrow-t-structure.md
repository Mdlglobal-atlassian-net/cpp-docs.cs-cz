---
title: nothrow_t – struktura
ms.date: 11/04/2016
f1_keywords:
- nothrow_t
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
ms.openlocfilehash: bd65b5006326850522a251cbcf7d655133a1aa8a
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245580"
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
