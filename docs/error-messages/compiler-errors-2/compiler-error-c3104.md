---
title: Chyba kompilátoru C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: b92a6eade137a1d319ec286afa08f8477ff029d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755855"
---
# <a name="compiler-error-c3104"></a>Chyba kompilátoru C3104

Neplatný argument atributu

Zadali jste neplatný argument atributu.

Další informace naleznete v tématu [typy parametrů atributu](../../extensions/attribute-parameter-types-cpp-component-extensions.md) .

Tato chyba se může vygenerovat v důsledku práce s shodami s kompilátorem, která se dokončila pro sadu Visual Studio 2005: při předávání spravovaných polí do vlastních atributů není typ pole už odvozený ze seznamu agregačních inicializací. Kompilátor nyní vyžaduje, abyste určili typ pole i seznam inicializátorů.

## <a name="example"></a>Příklad

Následující ukázka generuje C3104.

```cpp
// C3104a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104
// try the following line instead
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3104.

```cpp
// C3104b.cpp
// compile with: /clr /c
// C3104 expected
using namespace System;

int func() {
   return 0;
}

[attribute(All)]
ref class A {
public:
   A(int) {}
};

// Delete the following 2 lines to resolve.
[A(func())]
ref class B {};

// OK
[A(0)]
ref class B {};
```
