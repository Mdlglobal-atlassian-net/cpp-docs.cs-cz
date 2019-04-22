---
title: Explicitní přepsání (C++vyhodnocovací a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
ms.openlocfilehash: 7d36793e4467f9454aca1eb207f3c3dfbd483bff
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021421"
---
# <a name="explicit-overrides--ccli-and-ccx"></a>Explicitní přepsání (C++vyhodnocovací a C++/CX)

Toto téma popisuje postup explicitní přepsání člena základní třídy nebo rozhraní. Pojmenované přepsání (explicitně) by měla sloužit pouze k přepsání metody s Odvozená metoda, která má jiný název.

## <a name="all-runtimes"></a>Všechny moduly runtime

### <a name="syntax"></a>Syntaxe

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>Parametry

*overriding-function-declarator*<br/>
Návratový typ, název a argumentu seznamu přepisující funkce.  Všimněte si, že není nutné mít stejný název jako funkce přepsání přepisující funkce.

*type*<br/>
Základní typ, který obsahuje funkci, kterou chcete přepsat.

*– funkce*<br/>
Čárkami oddělený seznam jednoho nebo více názvy funkcí, které chcete přepsat.

*overriding-function-definition*<br/>
Příkazy tělo funkce, které definují přepisující funkce.

### <a name="remarks"></a>Poznámky

Použijte explicitní přepsání k vytvoření zástupce pro podpis metody a poskytují tak různé implementace pro pole stejnou signaturu metody.

Informace o úpravách chování se děděné typy a členy zděděných typů najdete v tématu [specifikátory přepisu](override-specifiers-cpp-component-extensions.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="remarks"></a>Poznámky

Informace o explicitních přepsáních ve nativní kód nebo kód zkompilovaný s `/clr:oldSyntax`, naleznete v tématu [explicitní přepsání](../cpp/explicit-overrides-cpp.md).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, jednoduché a implicitní přepsání a implementace členu základní rozhraní bez použití explicitní přepsání.

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

Následující příklad kódu ukazuje, jak implementovat všechny členy rozhraní s podpisem běžné pomocí syntaxe explicitního přepsání.

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

Následující příklad kódu ukazuje, jak přepsat funkce může mít jiný název funkce, které implementuje.

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

Následující příklad kódu ukazuje explicitní implementací rozhraní, která implementuje kolekce bezpečného typu.

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