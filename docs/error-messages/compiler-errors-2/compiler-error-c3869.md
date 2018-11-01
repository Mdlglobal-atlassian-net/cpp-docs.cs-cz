---
title: Chyba kompilátoru C3869
ms.date: 11/04/2016
f1_keywords:
- C3869
helpviewer_keywords:
- C3869
ms.assetid: 85b2ad72-95c1-4ed6-9761-6ef66c3802b7
ms.openlocfilehash: 1edc90c074389d6a666d3f01f6f7be424347f51a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428129"
---
# <a name="compiler-error-c3869"></a>Chyba kompilátoru C3869

v omezení gcnew chybí prázdný parametr seznam '().

`gcnew` Zvláštní omezení byl zadán bez prázdný seznam parametrů. Zobrazit [omezení parametrů obecných typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3869.

```
// C3869.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : gcnew   // C3869
// try the following line instead
// where T : gcnew()
ref class List {};
```