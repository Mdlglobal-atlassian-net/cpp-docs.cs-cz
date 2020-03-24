---
title: Chyba kompilátoru C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: 8ab2e0d152e4c123fa23512bc0111cebd070b3ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200860"
---
# <a name="compiler-error-c3409"></a>Chyba kompilátoru C3409

> prázdný blok atributu není povolený.

## <a name="remarks"></a>Poznámky

Hranaté závorky byly interpretovány kompilátorem jako blok [atributu](../../windows/attributes-alphabetical-reference.md) , ale nebyly nalezeny žádné atributy.

Kompilátor může tuto chybu generovat, pokud použijete hranaté závorky jako součást definice výrazu lambda. K této chybě dojde, pokud kompilátor nemůže určit, zda jsou hranaté závorky součástí definice výrazu lambda nebo bloku atributu. Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Pokud jsou hranaté závorky součástí bloku atributu:

   1. Zadejte jeden nebo více atributů v bloku atributu.

   1. Odeberte blok atributu.

1. Pokud jsou hranaté závorky součástí výrazu lambda, ujistěte se, že výraz lambda dodržuje platná pravidla syntaxe.

   Další informace o syntaxi výrazu lambda naleznete v tématu [syntaxe výrazu lambda](../../cpp/lambda-expression-syntax.md).

## <a name="example"></a>Příklad

Následující příklad generuje C3409.

```cpp
// C3409.cpp
// compile with: /c
#include <windows.h>
[]   // C3409
class a {};

// OK
[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface x {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class b : public x {};
```

## <a name="example"></a>Příklad

Následující příklad generuje C3409, protože lambda výraz používá specifikaci `mutable`, ale neposkytuje seznam parametrů. Kompilátor nemůže určit, zda jsou hranaté závorky součástí definice výrazu lambda nebo bloku atributu.

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>Viz také

[attribute](../../windows/attributes-alphabetical-reference.md)<br/>
[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Syntaxe výrazů lambda](../../cpp/lambda-expression-syntax.md)
