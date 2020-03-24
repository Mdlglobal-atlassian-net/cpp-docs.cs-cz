---
title: Upozornění kompilátoru C4986
ms.date: 11/04/2016
f1_keywords:
- C4986
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
ms.openlocfilehash: df6fc88ffe98dd2b4a3129800c7881f26d4f625b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164817"
---
# <a name="compiler-warning-c4986"></a>Upozornění kompilátoru C4986

' function ': specifikace výjimky neodpovídá předchozí deklaraci

Toto upozornění je možné vygenerovat, pokud existuje specifikace výjimky v jedné deklaraci a nikoli druhá.

Ve výchozím nastavení je C4986 vypnutý. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4986.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1()
{
    // ...
}
```

## <a name="example"></a>Příklad

Následující ukázka eliminuje toto upozornění.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1() throw (X*)
{
    // ...
}
```
