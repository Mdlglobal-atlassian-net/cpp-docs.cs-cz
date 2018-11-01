---
title: managed, unmanaged
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
ms.openlocfilehash: 0cc253ad7d0d4529340a13546f931075b0c7dfdc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473824"
---
# <a name="managed-unmanaged"></a>managed, unmanaged
Povolení řízení na úrovni funkce pro kompilování funkcí jako spravovaných nebo nespravovaných.

## <a name="syntax"></a>Syntaxe

```
#pragma managed
#pragma unmanaged
#pragma managed([push,] on | off)
#pragma managed(pop)
```

## <a name="remarks"></a>Poznámky

[/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru poskytuje řízení na úrovni modulu pro kompilování funkcí jako spravovaných nebo nespravovaných.

Nespravovaná funkce bude zkompilována pro nativní platformu a provádění části programu bude modulem CLR (Common Language Runtime) předáno nativní platformě.

Funkce jsou ve výchozím nastavení při použití `/clr` kompilovány jako spravované.

Při použití direktivy pragma:

- Přidání direktivy pragma před funkci, ale nikoliv do těla funkce.

- Přidání direktivy pragma po `#include` příkazy. Nepoužívejte direktivy pragma před `#include` příkazy.

Kompilátor ignoruje **spravované** a **nespravované** direktivy pragma Pokud `/clr` se nepoužívá při kompilaci.

Když je vytvořena instance funkce šablony, stav direktivy pragma v době definice šablony určuje, zda je spravovaná nebo nespravovaná.

Další informace najdete v tématu [inicializace smíšených sestavení](../dotnet/initialization-of-mixed-assemblies.md).

## <a name="example"></a>Příklad

```cpp
// pragma_directives_managed_unmanaged.cpp
// compile with: /clr
#include <stdio.h>

// func1 is managed
void func1() {
   System::Console::WriteLine("In managed function.");
}

// #pragma unmanaged
// push managed state on to stack and set unmanaged state
#pragma managed(push, off)

// func2 is unmanaged
void func2() {
   printf("In unmanaged function.\n");
}

// #pragma managed
#pragma managed(pop)

// main is managed
int main() {
   func1();
   func2();
}
```

```Output
In managed function.
In unmanaged function.
```

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)