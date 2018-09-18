---
title: Chyba kompilátoru C3704 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3704
dev_langs:
- C++
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4504534e3a53f37089f0b0ba045b7afde5a8065d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054984"
---
# <a name="compiler-error-c3704"></a>Chyba kompilátoru C3704

'function': metoda vararg nemůže aktivovat události

Pokusili jste se použít [__event](../../cpp/event.md) na metoda vararg. Chcete-li tuto chybu opravit, nahraďte `fireEvent(int i, ...)` volání s `fireEvent(int i)` volání, jak je znázorněno v následujícím příkladu kódu.

Následující ukázka generuje C3704:

```
// C3704.cpp
[ event_source(native) ]
class CEventSrc {
   public:
      __event void fireEvent(int i, ...);   // C3704
      // try the following line instead:
      // __event void fireEvent(int i);
};

int main() {
}
```