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
ms.openlocfilehash: 4e793f23581f7dc62a39fcd8c5c504fb5a2ccbc9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301467"
---
# <a name="__int8-__int16-__int32-__int64"></a>__int8, __int16, __int32, __int64

**Specifické pro společnost Microsoft**

Jazyk Microsoft C/C++ obsahuje podporu pro celočíselné typy s velikostí. Pomocí specifikátoru typu **__int**<em>n</em> můžete deklarovat 8, 16, 32 nebo 64 celočíselných proměnných, kde *n* je 8, 16, 32 nebo 64.

Následující příklad deklaruje jednu proměnnou pro každý z těchto celočíselných typů s velikostí:

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Typy **__int8**, **__int16**a **__int32** jsou synonyma pro typy ANSI, které mají stejnou velikost a jsou užitečné pro psaní přenositelného kódu, který se chová stejně jako napříč různými platformami. **__Int8** datový typ je synonymum typu **char**, **__int16** je synonymum typu **short**a **__int32** je synonym typu **int**. Typ **__int64** je synonymum s typem **Long Long**.

Z důvodu kompatibility s předchozími verzemi jsou **_int8**, **_int16**, **_int32**a **_int64** synonyma pro **__int8**, **__int16**, **__int32**a **__int64** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje, že parametr __int*XX* bude povýšen na **int**:

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Předdefinované typy](../cpp/fundamental-types-cpp.md)<br/>
[Rozsahy datových typů](../cpp/data-type-ranges.md)<br/>
