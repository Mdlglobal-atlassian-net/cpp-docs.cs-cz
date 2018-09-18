---
title: Upozornění kompilátoru C4439 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4439
dev_langs:
- C++
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 646b057f3f25bec8b686b08d50f0e473542ddcfc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076109"
---
# <a name="compiler-warning-c4439"></a>Upozornění kompilátoru C4439

'function': definice funkce se spravovaným typem v podpisu musí mít konvenci volání __clrcall

Kompilátor implicitně nahradit konvence volání s [__clrcall](../../cpp/clrcall.md). Pokud chcete vyřešit toto upozornění, odeberte `__cdecl` nebo `__stdcall` konvence volání.

C4439 je vždy vyvoláno jako chyba. Můžete vypnout toto upozornění se `#pragma warning` nebo **/wd**; naleznete v tématu [upozornění](../../preprocessor/warning.md) nebo [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md)Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C4439.

```
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```