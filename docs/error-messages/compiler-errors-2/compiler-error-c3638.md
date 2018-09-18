---
title: Chyba kompilátoru C3638 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3638
dev_langs:
- C++
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f1d135dd69155de39b097d59cf139eb47354d4f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107668"
---
# <a name="compiler-error-c3638"></a>Chyba kompilátoru C3638

'operator': nelze předefinovat standardní zabalení a rozbalení operátory převodu

Kompilátor definuje operátor převodu pro každé spravované třídy pro podporu implicitního zabalení. Tento operátor se nedá předefinovat.

Další informace najdete v tématu [implicitního zabalení](../../windows/boxing-cpp-component-extensions.md).

Následující ukázka generuje C3638:

```
// C3638.cpp
// compile with: /clr
value struct V {
   V(){}
   static operator V^(V);   // C3638
};

int main() {
   V myV;
   V ^ pmyV = myV;   // operator supports implicit boxing
}
```