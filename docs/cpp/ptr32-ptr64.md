---
title: __ptr32, __ptr64
ms.date: 10/09/2018
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
- __ptr32
- __ptr64
- _ptr32
- _ptr64
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
ms.openlocfilehash: c3ebe642284c6ee269dbfc39985630b7d949435f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179208"
---
# <a name="__ptr32-__ptr64"></a>__ptr32, __ptr64

**Specifické pro společnost Microsoft**

**__ptr32** představuje nativní ukazatel na 32 systém, zatímco **__ptr64** představuje nativní ukazatel na 64-bitový systém.

Následující příklad ukazuje, jak deklarovat jednotlivé typy ukazatelů:

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

V 32 bitovém systému je ukazatel deklarovaný pomocí **__ptr64** zkrácen na 32 ukazatel. V 64 bitovém systému je ukazatel deklarovaný pomocí **__ptr32** převeden na 64 ukazatel.

> [!NOTE]
> Při kompilaci s možností **/clr: Pure**nelze použít **__ptr32** ani **__ptr64** . V opačném případě se vygeneruje chyba kompilátoru C2472. Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

Z důvodu kompatibility s předchozími verzemi jsou **_ptr32** a **_ptr64** synonyma pro **__ptr32** a **__ptr64** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat a přidělit ukazatele pomocí **__ptr32** a **__ptr64** klíčová slova.

```cpp
#include <cstdlib>
#include <iostream>

int main()
{
    using namespace std;

    int * __ptr32 p32;
    int * __ptr64 p64;

    p32 = (int * __ptr32)malloc(4);
    *p32 = 32;
    cout << *p32 << endl;

    p64 = (int * __ptr64)malloc(4);
    *p64 = 64;
    cout << *p64 << endl;
}
```

```Output
32
64
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Předdefinované typy](../cpp/fundamental-types-cpp.md)
