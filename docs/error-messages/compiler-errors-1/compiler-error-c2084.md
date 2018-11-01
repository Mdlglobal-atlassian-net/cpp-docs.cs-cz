---
title: Chyba kompilátoru C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: 9aaf3a88e63234dfb842e4b48afd6e55595e96ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571311"
---
# <a name="compiler-error-c2084"></a>Chyba kompilátoru C2084

funkce "*funkce*' už má tělo.

Funkce již byl definován.

Ve verzích Visual C++ před Visual Studio 2002

- Kompilátor bude přijímat více specializace šablony, které přeložit na skutečný typ stejný, i když by nikdy nebude k dispozici další definice. Kompilátor zjistí nyní tyto několik definic.

- `__int32` a `int` zachází jako samostatné typy. Kompilátor nyní zpracovává `__int32` jako synonymum pro `int`. To znamená, že kompilátor zjistí víc definic, pokud je funkce přetížena u obou `__int32` a `int` a vrátí chybu.

## <a name="example"></a>Příklad

Následující ukázka generuje C2084:

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

Chcete-li tuto chybu opravit, odeberte duplicitní definice:

```
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```