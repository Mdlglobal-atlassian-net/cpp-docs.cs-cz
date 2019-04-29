---
title: Chybějící tělo funkce nebo proměnná
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 5e3436054d69da7fb67c240c1d684585734635c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378437"
---
# <a name="missing-function-body-or-variable"></a>Chybějící tělo funkce nebo proměnná

Právě prototypem funkce kompilátor může pokračovat bez chyb, ale linkeru nejde vyřešit volání na adresu, protože neexistuje žádný kód funkce nebo proměnná místa vyhrazeného. Tuto chybu neuvidíte, dokud nevytvoříte volání funkce, která musíte vyřešit linkeru.

## <a name="example"></a>Příklad

Volání funkce ve funkci main způsobí LNK2019, protože prototyp umožňuje kompilátoru myslíte, že existuje funkce.  Linker zjistí, že není.

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>Příklad

V jazyce C++ Ujistěte se, že složku zahrnujete implementace konkrétní funkce pro třídy a ne jenom prototypu v definici třídy. Pokud definujete třídu mimo rámec souborů záhlaví, nezapomeňte zahrnout název třídy před funkci (`Classname::memberfunction`).

```cpp
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

## <a name="see-also"></a>Viz také:

[Chyba linkerů LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)