---
title: "rozhraní – třída (C++ Component Extensions) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: interface_CPP
dev_langs: C++
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b3c6416ebe8b87295499e2a2ba50519d830b59ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="interface-class--c-component-extensions"></a>interface class (rozšíření komponent C++)
Deklaruje rozhraní.  Informace o nativní rozhraní najdete v tématu [__interface](../cpp/interface.md).  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 **Syntaxe**  
  
```  
  
interface_access  
interface class  
 name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};  
```  
  
 **Parametry**  
  
 *interface_access*  
 Usnadnění rozhraní mimo sestavení.  Možné hodnoty jsou **veřejné** a `private`.  `private`je výchozí.  Nemůže obsahovat vnořené rozhraní *interface_access* specifikátor.  
  
 *Jméno*  
 Název rozhraní.  
  
 *inherit_access*  
 Usnadnění přístupu *base_interface*.  Jediným povolené usnadnění pro základní rozhraní je `public` (výchozí).  
  
 *base_interface* (volitelné)  
 Základní rozhraní pro rozhraní *název*.  
  
 **Poznámky**  
  
 **Struktura rozhraní** je ekvivalentní **třída rozhraní**.  
  
 Rozhraní může obsahovat deklarace pro funkce, události a vlastnosti.  Všichni členové rozhraní mít veřejnou dostupnost. Rozhraní může také obsahovat členy statických dat, funkce, události a vlastnosti, a tyto statické členy musí být definován v rozhraní.  
  
 Rozhraní definuje, jak může implementovat třídu. Rozhraní není třídy a třídy mohou pouze implementovat rozhraní. Pokud třída definuje funkce deklarované v rozhraní, se implementuje funkce, není přepsán. Vyhledávání názvu proto nezahrnuje členové rozhraní.  
  
 Třídě nebo struktuře, která je odvozena z rozhraní musí implementovat rozhraní všechny členy. Při implementaci rozhraní *název* také musí implementovat rozhraní v `base_interface` seznamu.  
  
 Další informace naleznete v tématu:  
  
-   [Statický konstruktor rozhraní](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)  
  
-   [Obecná rozhraní (Visual C++)](../windows/generic-interfaces-visual-cpp.md)  
  
 Informace o jiných typech CLR najdete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md).  
  
 Pokud je rozhraní s typem, můžete zjistit v době kompilace `__is_interface_class(type)`. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 Ve vývojovém prostředí, můžete získat F1 – Nápověda na tato klíčová slova ve zvýraznění – klíčové slovo, (`interface class`, například) a stisknutím klávesy F1.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 **Poznámky**  
  
 (Existují žádné poznámky pro tuto funkci jazyka, která se týkají jenom prostředí Windows Runtime).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Poznámky**  
  
 (Existují žádné poznámky pro tuto funkci jazyka, která se týkají jenom modul common language runtime).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad kódu ukazuje, jak rozhraní můžete definovat chování funkce hodin.  
  
```  
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
  
 **Výstup**  
  
```Output  
in Function_3  
  
in Function_2  
  
in Function_1  
  
8  
  
OnClick: 7, 3.14159  
  
in Function_1  
```  
  
 **Příklad**  
  
 Následující příklad kódu ukazuje dva způsoby, jak implementovat funkce se stejným podpisem deklarován více rozhraní a použití těchto rozhraní třídou.  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)