---
title: Chyba kompilátoru C2084 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2084
dev_langs:
- C++
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09ce703b6908257e37c2b7ff1b2714f1426f941f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052104"
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