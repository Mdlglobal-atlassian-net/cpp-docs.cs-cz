---
title: __int8, __int16, __int32, __int64
ms.date: 10/09/2018
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
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
ms.openlocfilehash: b765eabcac3f9643c0cae78fefb6ce8231669ffc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183451"
---
# <a name="int8-int16-int32-int64"></a>__int8, __int16, __int32, __int64

**Microsoft Specific**

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
