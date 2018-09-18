---
title: Chybějící tělo funkce nebo proměnná | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a1337cf936d986c038aacc355490f13e5f0c2d8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088446"
---
# <a name="missing-function-body-or-variable"></a>Chybějící tělo funkce nebo proměnná

Právě prototypem funkce kompilátor může pokračovat bez chyb, ale linkeru nejde vyřešit volání na adresu, protože neexistuje žádný kód funkce nebo proměnná místa vyhrazeného. Tuto chybu neuvidíte, dokud nevytvoříte volání funkce, která musíte vyřešit linkeru.

## <a name="example"></a>Příklad

Volání funkce ve funkci main způsobí LNK2019, protože prototyp umožňuje kompilátoru myslíte, že existuje funkce.  Linker zjistí, že není.

```
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>Příklad

V jazyce C++ Ujistěte se, že složku zahrnujete implementace konkrétní funkce pro třídy a ne jenom prototypu v definici třídy. Pokud definujete třídu mimo rámec souborů záhlaví, nezapomeňte zahrnout název třídy před funkci (`Classname::memberfunction`).

```
// LNK2019_MFBV_2.cpp
// LNK2019 expected
struct A {
   static void Test();
};

// Should be void A::Test() {}
void Test() {}

int main() {
   A AObject;
   AObject.Test();
}
```

## <a name="see-also"></a>Viz také

[Chyba linkerů LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)