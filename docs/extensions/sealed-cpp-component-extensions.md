---
title: sealed (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
ms.openlocfilehash: ab5d5b32ceb87a3b1ccf08d170889dd4825f6c17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181795"
---
# <a name="sealed--ccli-and-ccx"></a>sealed (C++/CLI a C++/CX)

**sealed** je kontextové klíčové slovo pro referenční třídy, které označuje, že virtuální člen nelze přepsat nebo že typ nelze použít jako základní typ.

> [!NOTE]
> Standardní jazyk ISO C++ 11 zavedl klíčové slovo [Final](../cpp/final-specifier.md) . Použijte **finální** na standardních třídách a **zapečetěné** v referenčních třídách.

## <a name="all-runtimes"></a>Všechny moduly runtime

## <a name="syntax"></a>Syntaxe

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>Parametry

*RID*<br/>
Název funkce nebo třídy.

*návratový typ*<br/>
Typ, který je vrácen funkcí Function.

## <a name="remarks"></a>Poznámky

V první ukázce syntaxe je třída zapečetěná. Ve druhém příkladu je virtuální funkce zapečetěná.

Použijte klíčové slovo **sealed** pro třídy ref a jejich funkce virtuálních členů. Další informace naleznete v tématu [specifikátory přepisu a nativní kompilace](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Můžete detekovat v době kompilace, zda je typ zapečetěný pomocí vlastnosti typu `__is_sealed(type)`. Další informace naleznete v tématu [Podpora kompilátoru pro typové vlastnosti](compiler-support-for-type-traits-cpp-component-extensions.md).

**sealed** je kontextově závislé klíčové slovo.  Další informace najdete v tématu [Kontextově závislá klíčová slova](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

Viz [ref Classes a structs](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

(Neexistují žádné poznámky k této funkci jazyka, které platí pouze pro modul CLR (Common Language Runtime).)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad kódu ukazuje účinek **zapečetění** ve virtuálním členu.

```cpp
// sealed_keyword.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
   virtual void g();
};

ref class X : I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }

   virtual void g() sealed {
      System::Console::WriteLine("X::f override of I1::g");
   }
};

ref class Y : public X {
public:
   virtual void f() override {
      System::Console::WriteLine("Y::f override of I1::f");
   }

   /*
   // the following override generates a compiler error
   virtual void g() override {
      System::Console::WriteLine("Y::g override of I1::g");
   }
   */
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
   MyI -> g();

   I1 ^ MyI2 = gcnew Y;
   MyI2 -> f();
}
```

```Output
X::f override of I1::f
X::f override of I1::g
Y::f override of I1::f
```

Následující příklad kódu ukazuje, jak označit třídu jako zapečetěnou.

```cpp
// sealed_keyword_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X sealed : I1 {
public:
   virtual void f() override {}
};

ref class Y : public X {   // C3246 base class X is sealed
public:
   virtual void f() override {}
};
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
