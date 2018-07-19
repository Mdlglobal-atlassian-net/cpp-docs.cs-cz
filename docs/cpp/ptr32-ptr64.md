---
title: __ptr32 __ptr64 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
dev_langs:
- C++
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39078cfef6b327aee60d98fce6cccc0b69c5953b
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941701"
---
# <a name="ptr32-ptr64"></a>__ptr32, __ptr64

**Specifické pro Microsoft**

**__ptr32** představuje nativní ukazatel v 32bitovém systému, zatímco **__ptr64** představuje nativní ukazatel v 64bitovém systému.

Následující příklad ukazuje, jak deklarovat jednotlivé typy ukazatelů:

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

 V 32bitové verzi systému je ukazatel deklarovaný pomocí **__ptr64** zkrácen na 32bitový ukazatel. Na 64bitovém systému je ukazatel deklarovaný pomocí **__ptr32** převeden na 64bitový ukazatel.

> [!NOTE]
> Nemůžete použít **__ptr32** nebo **__ptr64** při kompilaci s **/CLR: pure**. V opačném případě bude vygenerována chyba kompilátoru C2472. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

- [Základní typy](../cpp/fundamental-types-cpp.md)