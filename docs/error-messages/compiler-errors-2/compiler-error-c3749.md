---
title: Chyba kompilátoru C3749 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3749
dev_langs:
- C++
helpviewer_keywords:
- C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4151d712c12cb34785c3f4ab77c76cdd78d4830
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024083"
---
# <a name="compiler-error-c3749"></a>Chyba kompilátoru C3749

'attribute': vlastního atributu nelze použít uvnitř funkce.

Vlastní atribut nelze použít uvnitř funkce. Další informace o vlastních atributů, naleznete v tématu [atribut](../../windows/attribute.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3749:

```
// C3749a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref struct ABC : public Attribute {
   ABC() {}
};

void f1() { [ABC]; };  // C3749
```
