---
title: Chyba kompilátoru C2341
ms.date: 11/04/2016
f1_keywords:
- C2341
helpviewer_keywords:
- C2341
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
ms.openlocfilehash: 4356182758398fa7ed1ec6a069affa4bb99ace1a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631683"
---
# <a name="compiler-error-c2341"></a>Chyba kompilátoru C2341

'název oddílu': segment musí být definován pomocí #pragma data_seg, code_seg nebo section použít

[Přidělit](../../cpp/allocate.md) příkazu odkazuje na segment, který ještě není definovaná pomocí [code_seg](../../preprocessor/code-seg.md), [data_seg](../../preprocessor/data-seg.md), nebo [části](../../preprocessor/section.md) direktivy pragma.

Následující ukázka generuje C2341:

```
// C2341.cpp
// compile with: /c
__declspec(allocate(".test"))   // C2341
int j = 1;
```

Možná řešení:

```
// C2341b.cpp
// compile with: /c
#pragma data_seg(".test")
__declspec(allocate(".test"))
int j = 1;
```