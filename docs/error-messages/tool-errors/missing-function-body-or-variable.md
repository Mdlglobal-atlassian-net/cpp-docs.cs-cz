---
title: Chybějící tělo funkce nebo proměnná
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 6d2ef22b90009d320485fb6fe3f7e308ae05c442
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173618"
---
# <a name="missing-function-body-or-variable"></a>Chybějící tělo funkce nebo proměnná

Pouze pomocí prototypu funkce může kompilátor pokračovat bez chyby, ale linker nemůže vyřešit volání na adresu, protože není k dispozici žádný kód funkce nebo vyhrazené místo proměnné. Tato chyba se nezobrazí, dokud nevytvoříte volání funkce, kterou musí linker přeložit.

## <a name="example"></a>Příklad

Volání funkce v main způsobí LINKERŮ LNK2019, protože prototyp umožňuje kompilátoru, aby se domnívá, že funkce existuje.  Linker zjistí, že není.

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>Příklad

V C++nástroji se ujistěte, že jste zahrnuli implementaci konkrétní funkce pro třídu, a ne pouze prototyp v definici třídy. Pokud definujete třídu mimo hlavičkový soubor, nezapomeňte zahrnout název třídy před funkci (`Classname::memberfunction`).

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

## <a name="see-also"></a>Viz také

[Chyba linkerů LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
