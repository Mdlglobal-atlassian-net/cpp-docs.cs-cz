---
title: Chyba kompilátoru C3869
ms.date: 11/04/2016
f1_keywords:
- C3869
helpviewer_keywords:
- C3869
ms.assetid: 85b2ad72-95c1-4ed6-9761-6ef66c3802b7
ms.openlocfilehash: 1a3d0d754557bbc811d1017ed1491181333e82dc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776467"
---
# <a name="compiler-error-c3869"></a>Chyba kompilátoru C3869

v omezení gcnew chybí prázdný parametr seznam '().

`gcnew` Zvláštní omezení byl zadán bez prázdný seznam parametrů. Zobrazit [omezení parametrů obecných typů (C++vyhodnocovací)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) Další informace.

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