---
title: Chyba kompilátoru C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: 302b21d709424cda50abd0247f7b82048511cd73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470587"
---
# <a name="compiler-error-c3813"></a>Chyba kompilátoru C3813

deklarace vlastnosti se může objevit jedině v definici spravované nebo typ WinRT

A [vlastnost](../../dotnet/how-to-use-properties-in-cpp-cli.md) lze deklarovat pouze v rámci spravované nebo prostředí Windows Runtime typu. Nativní typy se nepodporují `property` – klíčové slovo.

## <a name="example"></a>Příklad

Následující ukázka generuje C3813 a ukazuje, jak ho opravit:

```cpp
// C3813.cpp
// compile by using: cl /c /clr C3813.cpp
class A
{
   property int Int; // C3813
};

ref class B
{
   property int Int; // OK - declared within managed type
};
```