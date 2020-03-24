---
title: Chyba kompilátoru C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: c16ce501e25040a7ac7672a9ea131b4fe89570f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165610"
---
# <a name="compiler-error-c3813"></a>Chyba kompilátoru C3813

deklarace vlastnosti se může vyskytovat jenom v definici spravovaného nebo WinRT typu.

[Vlastnost](../../dotnet/how-to-use-properties-in-cpp-cli.md) může být deklarována pouze v rámci spravovaného nebo prostředí Windows Runtimeho typu. Nativní typy nepodporují klíčové slovo `property`.

## <a name="example"></a>Příklad

Následující ukázka generuje C3813 a ukazuje, jak ji opravit:

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
