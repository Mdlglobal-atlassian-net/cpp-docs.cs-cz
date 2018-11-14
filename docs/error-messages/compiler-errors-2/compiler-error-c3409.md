---
title: Chyba kompilátoru C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: b6ceb6f2e8700a5459dbd01db443ef90de314b5e
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330083"
---
# <a name="compiler-error-c3409"></a>Chyba kompilátoru C3409

> prázdný atribut block není povolený.

## <a name="remarks"></a>Poznámky

Hranaté závorky byly interpretovány kompilátorem jako [atribut](../../windows/cpp-attributes-reference.md) nebyly nalezeny bloku, ale žádné atributy.

Kompilátor může vygenerovat tuto chybu při použití hranaté závorky jako součást definice výraz lambda. Tato chyba nastane, pokud kompilátor nemůže určit, zda jsou hranaté závorky definici lambda výrazu nebo z bloku atributu. Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Pokud jsou hranaté závorky část z bloku atributu:

   1. Zadejte jeden nebo více atributů v bloku atributu.

   1. Odeberte blok atribut.

1. Pokud jsou hranaté závorky část výrazu lambda, ujistěte se, že výraz lambda následuje pravidla platnou syntaxi.

   Další informace o syntaxi výrazů lambda naleznete v tématu [Lambda Expression Syntax](../../cpp/lambda-expression-syntax.md).

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

Následující příklad generuje C3409, protože používá výraz lambda `mutable` specifikace, ale neposkytuje seznam parametrů. Kompilátor nemůže určit, zda jsou hranaté závorky definici lambda výrazu nebo z bloku atributu.

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>Viz také

[attribute](../../windows/cpp-attributes-reference.md)<br/>
[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Syntaxe výrazů lambda](../../cpp/lambda-expression-syntax.md)