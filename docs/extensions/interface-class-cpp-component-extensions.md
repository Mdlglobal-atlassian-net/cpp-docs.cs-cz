---
title: Třída rozhraní (C + +/ CLI a C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- interface_CPP
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
ms.openlocfilehash: 60e8965e3ef2538554d8c664b35bd0849bd5e69e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035855"
---
# <a name="interface-class--ccli-and-ccx"></a>Třída rozhraní (C + +/ CLI a C + +/ CX)

Deklaruje rozhraní.  Informace o nativní rozhraní, naleznete v tématu [__interface](../cpp/interface.md).

## <a name="all-runtimes"></a>Všechny moduly runtime

### <a name="syntax"></a>Syntaxe

```cpp
interface_access
interface class
name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};
```

### <a name="parameters"></a>Parametry

*interface_access*<br/>
Usnadnění rozhraní mimo sestavení.  Možné hodnoty jsou **veřejné** a **privátní**.  **privátní** je výchozí nastavení. Vnořené rozhraní nemůže mít *interface_access* specifikátor.

*name*<br/>
Název rozhraní.

*inherit_access*<br/>
Přístupnost *base_interface*.  Pouze povoleno usnadnění pro základní rozhraní není **veřejné** (výchozí).

*base_interface*<br/>
(Volitelné) Základní rozhraní pro rozhraní *název*.

### <a name="remarks"></a>Poznámky

**Struktura rozhraní** je ekvivalentní **třída rozhraní**.

Rozhraní může obsahovat deklarace pro funkce, události a vlastnosti.  Všechny členy rozhraní mít veřejnou přístupnost. Rozhraní může také obsahovat statických datových členů, funkcí, události a vlastnosti, a tyto statické členy musí být definován v rozhraní.

Rozhraní definuje, jak se může implementovat třídu. Rozhraní není třídy a třídy lze implementovat pouze rozhraní. Pokud třída definuje funkce deklarovaná v rozhraní, že funkce je implementovaná, nebyly přepsány. Vyhledávání názvu proto nezahrnuje členy rozhraní.

Třída nebo struktura, která je odvozena z rozhraní musí implementovat všechny členy rozhraní. Při implementaci rozhraní *název* musí také implementovat rozhraní v `base_interface` seznamu.

Další informace naleznete v tématu:

- [Statický konstruktor rozhraní](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

- [Obecná rozhraní (C + +/ CLI)](generic-interfaces-visual-cpp.md)

Informace o dalších typech CLR naleznete v tématu [třídy a struktury](classes-and-structs-cpp-component-extensions.md).

Pokud je typ rozhraní, můžete zjistit v době kompilace `__is_interface_class(type)`. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](compiler-support-for-type-traits-cpp-component-extensions.md).

Ve vývojovém prostředí, můžete získat nápovědy klávesy F1 v těchto klíčových slov zvýrazněním klíčového slova (`interface class`, třeba) a stisknutím klávesy F1.

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="remarks"></a>Poznámky

(Neexistují žádné poznámky o této funkci jazyka, které se vztahují jenom Windows Runtime.)

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="remarks"></a>Poznámky

(Neexistují žádné poznámky o této funkci jazyka, které se vztahují pouze modul common language runtime.)

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, jak definovat chování clock – funkce rozhraní.

```cpp
// mcppv2_interface_class.cpp
// compile with: /clr
using namespace System;

public delegate void ClickEventHandler(int, double);

// define interface with nested interface
public interface class Interface_A {
   void Function_1();

   interface class Interface_Nested_A {
      void Function_2();
   };
};

// interface with a base interface
public interface class Interface_B : Interface_A {
   property int Property_Block;
   event ClickEventHandler^ OnClick;
   static void Function_3() { Console::WriteLine("in Function_3"); }
};

// implement nested interface
public ref class MyClass : public Interface_A::Interface_Nested_A {
public:
   virtual void Function_2() { Console::WriteLine("in Function_2"); }
};

// implement interface and base interface
public ref class MyClass2 : public Interface_B {
private:
   int MyInt;

public:
   // implement non-static function
   virtual void Function_1() { Console::WriteLine("in Function_1"); }

   // implement property
   property int Property_Block {
      virtual int get() { return MyInt; }
      virtual void set(int value) { MyInt = value; }
   }
   // implement event
   virtual event ClickEventHandler^ OnClick;

   void FireEvents() {
      OnClick(7, 3.14159);
   }
};

// class that defines method called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }
};

int main() {
   // call static function in an interface
   Interface_B::Function_3();

   // instantiate class that implements nested interface
   MyClass ^ x = gcnew MyClass;
   x->Function_2();

   // instantiate class that implements interface with base interface
   MyClass2 ^ y = gcnew MyClass2;
   y->Function_1();
   y->Property_Block = 8;
   Console::WriteLine(y->Property_Block);

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   y->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // invoke events
   y->FireEvents();

   // unhook handler to event
   y->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // call implemented function via interface handle
   Interface_A^ hi = gcnew MyClass2();
   hi->Function_1();
}
```

```Output
in Function_3

in Function_2

in Function_1

8

OnClick: 7, 3.14159

in Function_1
```

Následující příklad kódu ukazuje dva způsoby, jak implementovat funkce se stejnou signaturou, které jsou deklarovány ve více rozhraní a použití těchto rozhraní pomocí třídy.

```cpp
// mcppv2_interface_class_2.cpp
// compile with: /clr /c
interface class I {
   void Test();
   void Test2();
};

interface class J : I {
   void Test();
   void Test2();
};

ref struct R : I, J {
   // satisfies the requirement to implement Test in both interfaces
   virtual void Test() {}

   // implement both interface functions with explicit overrides
   virtual void A() = I::Test2 {}
   virtual void B() = J::Test2 {}
};
```

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)