---
title: Chyba kompilátoru C2157 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2157
dev_langs:
- C++
helpviewer_keywords:
- C2157
ms.assetid: babbca24-16dc-4b69-be14-a675029249c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd17b03cc48555800e3c36cc3f5512506f011372
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072061"
---
# <a name="compiler-error-c2157"></a>Chyba kompilátoru C2157

'function': musí být deklarované před použitím v seznamu direktiv pragma

Název funkce není deklarován před kterou se odkazuje v seznamu funkcí pro [alloc_text](../../preprocessor/alloc-text.md) direktivy pragma.

Následující ukázka generuje C2157:

```
// C2157.cpp
// compile with: /c
#pragma alloc_text( "func", func)   // C2157

// OK
extern "C" void func();
#pragma alloc_text( "func", func)
```