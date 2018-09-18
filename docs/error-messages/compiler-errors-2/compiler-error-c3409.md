---
title: Chyba kompilátoru C3409 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3409
dev_langs:
- C++
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 338a98adb45ee9fc8eb392853a5693d10a171940
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058832"
---
# <a name="compiler-error-c3409"></a>Chyba kompilátoru C3409

prázdný atribut block není povolený.

Hranaté závorky byly interpretovány kompilátorem jako [atribut](../../windows/cpp-attributes-reference.md) nebyly nalezeny bloku, ale žádné atributy.

Kompilátor může vygenerovat tuto chybu při použití hranaté závorky jako součást definice výraz lambda. Tato chyba nastane, pokud kompilátor nemůže určit, zda jsou hranaté závorky definici lambda výrazu nebo z bloku atributu. Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Pokud jsou hranaté závorky část z bloku atributu:

   1. Zadejte jeden nebo více atributů v bloku atributu.

   1. Odeberte blok atribut.

1. Pokud jsou hranaté závorky část výrazu lambda:

   1. Ujistěte se, že výraz lambda následuje pravidla platnou syntaxi.

         Další informace o syntaxi výrazů lambda naleznete v tématu [Lambda Expression Syntax](../../cpp/lambda-expression-syntax.md).

    2.

## <a name="example"></a>Příklad

Následující příklad generuje C3409.

```
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

```
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