---
title: managed, unmanaged – direktivy pragma
ms.date: 08/29/2019
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
ms.openlocfilehash: 4c13155d1c84966a593df11baf525a0c3539f02c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218808"
---
# <a name="managed-unmanaged-pragmas"></a>managed, unmanaged – direktivy pragma

Povolit řízení na úrovni funkce pro kompilaci funkcí jako spravovaných nebo nespravovaných.

## <a name="syntax"></a>Syntaxe

> **#pragma spravované**\
> **nespravované #pragma**\
> **#pragma spravované (**  | [ **push,** ] {**off** } **)** \
> **spravované #pragma (pop)**

## <a name="remarks"></a>Poznámky

Možnost kompilátoru [/CLR](../build/reference/clr-common-language-runtime-compilation.md) poskytuje ovládací prvky na úrovni modulu pro kompilaci funkcí buď jako spravované, nebo nespravované.

Nespravovaná funkce bude zkompilována pro nativní platformu. Provádění této části programu bude modulem CLR (Common Language Runtime) předáno nativní platformě.

Funkce jsou ve výchozím nastavení při použití `/clr` kompilovány jako spravované.

Při použití těchto direktiv pragma:

- Přidejte direktivu pragma před funkci, ale ne uvnitř těla funkce.

- Přidejte direktivu pragma `#include` po příkazech. Tyto direktivy pragma Nepoužívejte `#include` před příkazy.

Kompilátor ignoruje **spravované** a nespravované direktivy pragma `/clr` , pokud se v kompilaci nepoužívá.

Při vytvoření instance funkce šablony určuje, zda je stav direktiva pragma při definování šablony, pokud je spravovaný nebo nespravovaný.

Další informace naleznete v tématu [inicializace smíšených sestavení](../dotnet/initialization-of-mixed-assemblies.md).

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

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
