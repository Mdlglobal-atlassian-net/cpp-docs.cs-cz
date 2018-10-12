---
title: __int8, __int16, __int32 __int64 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
- __int8
- __int16
- __int32
- __int64
- _int8
- _int16
- _int32
- _int64
dev_langs:
- C++
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b639e7a65bbe206d029a5ba28109170cb0f6a610
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163540"
---
# <a name="int8-int16-int32-int64"></a>__int8, __int16, __int32, __int64

**Specifické pro Microsoft**

Jazyk Microsoft C/C++ obsahuje podporu pro celočíselné typy s velikostí. Je možné deklarovat 8, 16, 32- a 64bitové celočíselné proměnné pomocí **__int**<em>n</em> zadejte specifikátor, kde *n* je 8, 16, 32 nebo 64.

Následující příklad deklaruje jednu proměnnou pro každý z těchto celočíselných typů s velikostí:

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Typy **__int8**, **__int16**, a **__int32** jsou synonyma pro typy ANSI stejné velikosti a jsou užitečné pro psaní přenositelného kódu, který se chová stejně jako na různých platformách. **__Int8** datový typ je synonymum pro typ **char**, **__int16** je synonymem typu **krátký**, a **__int32**  je synonymem typu **int**. **__Int64** typ je synonymum pro typ **long long**.

Z důvodu kompatibility s předchozími verzemi **_int8**, **_int16**, **_int32**, a **_int64** jsou synonyma pro **__int8** , **__int16**, **__int32**, a **__int64** Pokud – možnost kompilátoru [/Za \(zakázat jazyka rozšíření)](../build/reference/za-ze-disable-language-extensions.md) určena.

## <a name="example"></a>Příklad

Následující příklad ukazuje, že __int*xx* parametr bude povýšen na **int**:

```cpp
// sized_int_types.cpp

#include <stdio.h>

void func(int i) {
    printf_s("%s\n", __FUNCTION__);
}

int main()
{
    __int8 i8 = 100;
    func(i8);   // no void func(__int8 i8) function
                // __int8 will be promoted to int
}
```

```Output
func
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Základní typy](../cpp/fundamental-types-cpp.md)<br/>
[Rozsahy datových typů](../cpp/data-type-ranges.md)<br/>
