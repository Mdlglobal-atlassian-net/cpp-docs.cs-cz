---
title: Explicitní přepsání (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
ms.openlocfilehash: b80e49489c0b0d26469ba9f8b77e80a962668e35
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821635"
---
# <a name="explicit-overrides--ccli-and-ccx"></a>Explicitní přepsání (C++/CLI a C++/CX)

Toto téma popisuje, jak explicitně přepsat člena základní třídy nebo rozhraní. Pojmenované (explicitní) přepsání by mělo být použito pouze k přepsání metody s odvozenou metodou, která má jiný název.

## <a name="all-runtimes"></a>Všechny moduly runtime

### <a name="syntax"></a>Syntaxe

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>Parametry

*overriding-function-declarator*<br/>
Návratový typ, název a seznam argumentů přepisování funkce.  Všimněte si, že přepsání funkce nemusí mít stejný název jako funkce, která je přepsána.

*type*<br/>
Základní typ, který obsahuje funkci, která má být přepsána.

*slouží*<br/>
Seznam jednoho nebo více názvů funkcí, které mají být přepsány čárkami oddělenými čárkami.

*přepsání – definice funkce*<br/>
Příkazy těla funkce, které definují funkci přepsání.

### <a name="remarks"></a>Poznámky

Pomocí explicitního přepsání můžete vytvořit alias pro podpis metody nebo poskytnout různé implementace pro metody se stejnou signaturou.

Informace o změně chování zděděných typů a zděděných členů typu naleznete v tématu [specifikátory přepisu](override-specifiers-cpp-component-extensions.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="remarks"></a>Poznámky

Informace o explicitních přepsáních v nativním kódu nebo kódu kompilovaném pomocí `/clr:oldSyntax`naleznete v tématu [Explicit Overrides](../cpp/explicit-overrides-cpp.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad kódu ukazuje jednoduché, implicitní přepsání a implementaci člena v základním rozhraní bez použití explicitních přepsání.

```cpp
// explicit_override_1.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
}
```

```Output
X::f override of I1::f
```

Následující příklad kódu ukazuje, jak implementovat všechny členy rozhraní se společným podpisem pomocí syntaxe explicitního přepsání.

```cpp
// explicit_override_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

interface struct I2 {
   virtual void f();
};

ref struct X : public I1, I2 {
   virtual void f() = I1::f, I2::f {
      System::Console::WriteLine("X::f override of I1::f and I2::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   I2 ^ MyI2 = gcnew X;
   MyI -> f();
   MyI2 -> f();
}
```

```Output
X::f override of I1::f and I2::f
X::f override of I1::f and I2::f
```

Následující příklad kódu ukazuje, jak přepsání funkce může mít jiný název než funkce, kterou implementuje.

```cpp
// explicit_override_3.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void g() = I1::f {
      System::Console::WriteLine("X::g");
   }
};

int main() {
   I1 ^ a = gcnew X;
   a->f();
}
```

```Output
X::g
```

Následující příklad kódu ukazuje explicitní implementaci rozhraní, která implementuje typově bezpečnou kolekci.

```cpp
// explicit_override_4.cpp
// compile with: /clr /LD
using namespace System;
ref class R : ICloneable {
   int X;

   virtual Object^ C() sealed = ICloneable::Clone {
      return this->Clone();
   }

public:
   R() : X(0) {}
   R(int x) : X(x) {}

   virtual R^ Clone() {
      R^ r = gcnew R;
      r->X = this->X;
      return r;
   }
};
```

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)