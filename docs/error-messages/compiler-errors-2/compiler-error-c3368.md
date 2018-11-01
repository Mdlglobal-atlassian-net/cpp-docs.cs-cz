---
title: Chyba kompilátoru C3368
ms.date: 11/04/2016
f1_keywords:
- C3368
helpviewer_keywords:
- C3368
ms.assetid: 5bfd5be4-dfa9-4b33-9612-010561b40955
ms.openlocfilehash: f027e2707dc677d93567f91307e9dcfcb8dd682f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582309"
---
# <a name="compiler-error-c3368"></a>Chyba kompilátoru C3368

deklaraci funkce: Neplatná konvence volání pro IDL

Můžete použít pouze [__stdcall](../../cpp/stdcall.md) nebo [__cdecl](../../cpp/cdecl.md) konvencí volání v souboru IDL.

Následující ukázka generuje C3368:

```
// C3368.cpp
// processor: x86
[idl_module(name="Name", dllname="Some.dll")];

[idl_module(name="Name")]
int __fastcall f1();   // C3368
```