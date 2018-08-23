---
title: zapečetěné (rozšíření komponent C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9693e16695d7a8c755515b4dd5163e2688a1d29
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611286"
---
# <a name="sealed--c-component-extensions"></a>sealed (rozšíření komponent C++)

**zapečetěné** jako kontextové klíčové slovo pro referenční třídy, která označuje, že virtuální člen nelze přepsat, nebo typ nelze použít jako základní typ.

> [!NOTE]
> C ++ 11 jazyka podle standardu ISO má [konečné](../cpp/final-specifier.md) – klíčové slovo, což je podporováno v sadě Visual Studio. Použití **konečné** na standardní třídy a **zapečetěné** na referenční třídy.

## <a name="all-runtimes"></a>Všechny moduly runtime

## <a name="syntax"></a>Syntaxe

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>Parametry

*identifikátor*  
Název třídy nebo funkce.

*Návratový typ*  
Typ, který je vrácen funkce.

## <a name="remarks"></a>Poznámky

V prvním příkladu syntaxe je zapečetěná třída. V druhém příkladu je zapečetěná virtuální funkce.

**Zapečetěné** – klíčové slovo je platný pro nativní cíle a také pro prostředí Windows Runtime a common language runtime (CLR). Další informace najdete v tématu [specifikátory přepisu a nativní kompilace](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

V době kompilace může zjistit, zda typ je zapečetěný pomocí `__is_sealed(type)` typovou vlastnost. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

**zapečetěné** je kontextové klíčové slovo.  Další informace najdete v tématu [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

Zobrazit [referenční třídy a struktury](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

(Neexistují žádné poznámky o této funkci jazyka, které se vztahují pouze modul common language runtime.)

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Tento příklad kódu ukazuje účinek **zapečetěné** na člena virtuální.

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

Následující příklad kódu ukazuje, jak označit třídu jako zapečetěný.

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

[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)