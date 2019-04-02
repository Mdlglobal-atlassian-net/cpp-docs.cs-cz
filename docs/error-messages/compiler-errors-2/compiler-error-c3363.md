---
title: Chyba kompilátoru C3363
ms.date: 11/04/2016
f1_keywords:
- C3363
helpviewer_keywords:
- C3363
ms.assetid: 41aa922f-608e-4f7a-ba66-451fc1161935
ms.openlocfilehash: eca598233dbe4cae4730e952b45945653ec8ffaa
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775501"
---
# <a name="compiler-error-c3363"></a>Chyba kompilátoru C3363

'type': 'identifikátor typeid' lze použít pouze na typ

[Typeid](../../extensions/typeid-cpp-component-extensions.md) operátor nebyl použit správně.

## <a name="example"></a>Příklad

Následující ukázka generuje C3363.

```
// C3363.cpp
// compile with: /clr
int main() {
   System::typeid;   // C3363
}
```