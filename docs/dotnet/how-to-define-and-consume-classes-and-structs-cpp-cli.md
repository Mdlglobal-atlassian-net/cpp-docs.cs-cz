---
title: "Postupy: definování a používání tříd a struktur (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a0a276854c9f2e27439c2c16e9299d4eaa9243d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Postupy: Definice a používání tříd a struktur (C++/CLI)
Tento článek ukazuje, jak definovat a využívat uživatelem definované odkazové a hodnotové typy v jazyce C + +/ CLI.  
  
##  <a name="BKMK_Contents"></a>Obsah  
 [Vytvoření instance objektu](#BKMK_Object_instantiation)  
  
 [Implicitně abstraktní třídy](#BKMK_Implicitly_abstract_classes)  
  
 [Viditelnost typů](#BKMK_Type_visibility)  
  
 [Viditelnost členů](#BKMK_Member_visibility)  
  
 [Veřejné a privátní nativních tříd](#BKMK_Public_and_private_native_classes)  
  
 [Statické konstruktory](#BKMK_Static_constructors)  
  
 [Sémantika této ukazatele](#BKMK_Semantics_of_the_this_pointer)  
  
 [Funkce skrytí podle podpisu](#BKMK_Hide_by_signature_functions)  
  
 [Kopírovací konstruktory](#BKMK_Copy_constructors)  
  
 [Destruktory a finalizační metody](#BKMK_Destructors_and_finalizers)  
  
##  <a name="BKMK_Object_instantiation"></a>Vytvoření instance objektu  
 Typy odkazů (ref) a typy hodnot se dá jenom vytvořit instance na spravované haldě, není v zásobníku nebo v haldě nativní.  
  
```  
// mcppv2_ref_class2.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   int i;  
  
   // nested class  
   ref class MyClass2 {  
   public:  
      int i;  
   };  
  
   // nested interface  
   interface struct MyInterface {  
      void f();  
   };  
};  
  
ref class MyClass2 : public MyClass::MyInterface {  
public:  
   virtual void f() {  
      System::Console::WriteLine("test");  
   }  
};  
  
public value struct MyStruct {  
   void f() {  
      System::Console::WriteLine("test");  
   }     
};  
  
int main() {  
   // instantiate ref type on garbage-collected heap  
   MyClass ^ p_MyClass = gcnew MyClass;  
   p_MyClass -> i = 4;  
  
   // instantiate value type on garbage-collected heap  
   MyStruct ^ p_MyStruct = gcnew MyStruct;  
   p_MyStruct -> f();  
  
   // instantiate value type on the stack  
   MyStruct p_MyStruct2;  
   p_MyStruct2.f();  
  
   // instantiate nested ref type on garbage-collected heap  
   MyClass::MyClass2 ^ p_MyClass2 = gcnew MyClass::MyClass2;  
   p_MyClass2 -> i = 5;  
}  
```  
  
##  <a name="BKMK_Implicitly_abstract_classes"></a>Implicitně abstraktní třídy  
 *Implicitně abstraktní třídy* nelze vytvořit instanci. Pokud základní typ třídy rozhraní a třídy neimplementuje všechny funkce člen rozhraní je implicitně abstraktní třídu.  
  
 Pokud není možné vytvořit objekty z třídy, která je odvozena z rozhraní, může být z důvodu, že třída je implicitně abstraktní. Další informace o abstraktní třídy najdete v tématu [abstraktní](../windows/abstract-cpp-component-extensions.md).  
  
 Následující příklad kódu ukazuje, který `MyClass` třída nelze vytvořit instance, protože funkce `MyClass::func2` není implementována. Chcete-li povolit příklad zkompilovat, zrušte komentář u `MyClass::func2`.  
  
```  
// mcppv2_ref_class5.cpp  
// compile with: /clr  
interface struct MyInterface {  
   void func1();  
   void func2();  
};  
  
ref class MyClass : public MyInterface {  
public:  
   void func1(){}  
   // void func2(){}  
};  
  
int main() {  
   MyClass ^ h_MyClass = gcnew MyClass;   // C2259   
                                          // To resolve, uncomment MyClass::func2.  
}  
```  
  
##  <a name="BKMK_Type_visibility"></a>Viditelnost typů  
 Viditelnost běžné typy language runtime (CLR) můžete řídit, takže pokud je sestavení odkazováno, typy v sestavení může být viditelné nebo mimo sestavení nejsou viditelné.  
  
 `public`Označuje, že je viditelná pro zdrojový soubor, který obsahuje typ `#using` pro sestavení, které obsahuje typ direktivy.  `private`Označuje, že typ není viditelná pro zdrojové soubory, které obsahují `#using` pro sestavení, které obsahuje typ direktivy. Privátní typy jsou však viditelné v rámci stejného sestavení. Ve výchozím nastavení, je viditelnost pro třídu `private`.  
  
 Ve výchozím nastavení před Visual C++ 2005 měl nativní typy veřejnou dostupnost mimo sestavení. Povolit [upozornění kompilátoru (úroveň 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) můžete zobrazit, kde jsou nesprávně použity privátní nativní typy. Použití [make_public –](../preprocessor/make-public.md) – Direktiva pragma předat veřejnou dostupnost nativního typu v souboru zdrojového kódu, který nelze změnit.  
  
 Další informace najdete v tématu [#using – direktiva](../preprocessor/hash-using-directive-cpp.md).  
  
 Následující příklad ukazuje, jak deklarujte typy a zadat jejich usnadnění a poté přístup k tyto typy v sestavení. Samozřejmě, pokud je sestavení, který má privátní typy odkazován pomocí `#using`, pouze veřejné typy v sestavení jsou viditelné.  
  
```  
// type_visibility.cpp  
// compile with: /clr  
using namespace System;  
// public type, visible inside and outside assembly  
public ref struct Public_Class {  
   void Test(){Console::WriteLine("in Public_Class");}  
};  
  
// private type, visible inside but not outside assembly  
private ref struct Private_Class {  
   void Test(){Console::WriteLine("in Private_Class");}  
};  
  
// default accessibility is private  
ref class Private_Class_2 {  
public:  
   void Test(){Console::WriteLine("in Private_Class_2");}  
};  
  
int main() {  
   Public_Class ^ a = gcnew Public_Class;  
   a->Test();  
  
   Private_Class ^ b = gcnew Private_Class;  
   b->Test();  
  
   Private_Class_2 ^ c = gcnew Private_Class_2;  
   c->Test();  
}  
```  
  
 **Output**  
  
```Output  
in Public_Class  
in Private_Class  
in Private_Class_2  
```  
  
 Nyní Pojďme přepište v předchozím příkladu tak, aby je vytvořen jako knihovny DLL.  
  
```  
// type_visibility_2.cpp  
// compile with: /clr /LD  
using namespace System;  
// public type, visible inside and outside the assembly  
public ref struct Public_Class {  
   void Test(){Console::WriteLine("in Public_Class");}  
};  
  
// private type, visible inside but not outside the assembly  
private ref struct Private_Class {  
   void Test(){Console::WriteLine("in Private_Class");}  
};  
  
// by default, accessibility is private  
ref class Private_Class_2 {  
public:  
   void Test(){Console::WriteLine("in Private_Class_2");}  
};  
```  
  
 Další příklad ukazuje postup přístup k typům mimo sestavení. V této ukázce spotřebuje klienta komponentu, která je vestavěná v předchozím příkladu.  
  
```  
// type_visibility_3.cpp  
// compile with: /clr  
#using "type_visibility_2.dll"  
int main() {  
   Public_Class ^ a = gcnew Public_Class;  
   a->Test();  
  
   // private types not accessible outside the assembly  
   // Private_Class ^ b = gcnew Private_Class;  
   // Private_Class_2 ^ c = gcnew Private_Class_2;  
}  
```  
  
 **Output**  
  
```Output  
in Public_Class  
```  
  
##  <a name="BKMK_Member_visibility"></a>Viditelnost členů  
 Můžete provést přístupu členem veřejnou třídu z v rámci stejného sestavení liší od přístup k němu z mimo sestavení pomocí párů specifikátory přístupu `public`, `protected`, a`private`  
  
 Tato tabulka shrnuje účinek různých specifikátory přístupu:  
  
|Specifikátor|Efekt|  
|---------------|------------|  
|public|Člen je přístupná uvnitř i vně sestavení.  V tématu [veřejné](../cpp/public-cpp.md) Další informace.|  
|private|Člen není dostupný, ani mimo sestavení.  V tématu [privátní](../cpp/private-cpp.md) Další informace.|  
|protected|Člen je přístupná uvnitř i vně sestavení, ale jenom pro odvozené typy.  V tématu [chráněné](../cpp/protected-cpp.md) Další informace.|  
|internal|Člen je veřejný uvnitř sestavení, ale privátní mimo sestavení.  `internal`je kontextová – klíčové slovo.  Další informace najdete v tématu [klíčová slova Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md).|  
|veřejné chráněné - nebo - chráněné veřejné|Člen je veřejný uvnitř sestavení, ale chráněné mimo sestavení.|  
|privátní chráněné - nebo - chráněné privátní|Člen je chráněný uvnitř sestavení, ale privátní mimo sestavení.|  
  
 Následující příklad ukazuje veřejného typu, který má členy, které jsou deklarovány s jinou přístupnosti a potom zobrazí přístup k těmto členům z uvnitř sestavení.  
  
```  
  
// compile with: /clr  
using namespace System;  
// public type, visible inside and outside the assembly  
public ref class Public_Class {  
public:  
   void Public_Function(){System::Console::WriteLine("in Public_Function");}  
  
private:  
   void Private_Function(){System::Console::WriteLine("in Private_Function");}  
  
protected:  
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}  
  
internal:  
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}  
  
protected public:  
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}  
  
public protected:  
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}  
  
private protected:  
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}  
  
protected private:  
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}  
};  
  
// a derived type, calls protected functions  
ref struct MyClass : public Public_Class {  
   void Test() {  
      Console::WriteLine("=======================");  
      Console::WriteLine("in function of derived class");  
      Protected_Function();  
      Protected_Private_Function();  
      Private_Protected_Function();  
      Console::WriteLine("exiting function of derived class");  
      Console::WriteLine("=======================");  
   }  
};  
  
int main() {  
   Public_Class ^ a = gcnew Public_Class;  
   MyClass ^ b = gcnew MyClass;  
   a->Public_Function();  
   a->Protected_Public_Function();  
   a->Public_Protected_Function();  
  
   // accessible inside but not outside the assembly  
   a->Internal_Function();  
  
   // call protected functions  
   b->Test();  
  
   // not accessible inside or outside the assembly  
   // a->Private_Function();  
}  
```  
  
 **Output**  
  
```Output  
in Public_Function  
in Protected_Public_Function  
in Public_Protected_Function  
in Internal_Function  
=======================  
in function of derived class  
in Protected_Function  
in Protected_Private_Function  
in Private_Protected_Function  
exiting function of derived class  
=======================  
```  
  
 Nyní Vytvořme v předchozím příkladu jako knihovny DLL.  
  
```  
  
// compile with: /clr /LD  
using namespace System;  
// public type, visible inside and outside the assembly  
public ref class Public_Class {  
public:  
   void Public_Function(){System::Console::WriteLine("in Public_Function");}  
  
private:  
   void Private_Function(){System::Console::WriteLine("in Private_Function");}  
  
protected:  
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}  
  
internal:  
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}  
  
protected public:  
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}  
  
public protected:  
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}  
  
private protected:  
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}  
  
protected private:  
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}  
};  
  
// a derived type, calls protected functions  
ref struct MyClass : public Public_Class {  
   void Test() {  
      Console::WriteLine("=======================");  
      Console::WriteLine("in function of derived class");  
      Protected_Function();  
      Protected_Private_Function();  
      Private_Protected_Function();  
      Console::WriteLine("exiting function of derived class");  
      Console::WriteLine("=======================");  
   }  
};  
```  
  
 Následující ukázka spotřebuje komponentu, který je vytvořen v předchozí ukázce a tím ukazuje, jak přístup ke členům z mimo sestavení.  
  
```  
  
// compile with: /clr  
#using "type_member_visibility_2.dll"  
using namespace System;  
// a derived type, calls protected functions  
ref struct MyClass : public Public_Class {  
   void Test() {  
      Console::WriteLine("=======================");  
      Console::WriteLine("in function of derived class");  
      Protected_Function();  
      Protected_Public_Function();  
      Public_Protected_Function();  
      Console::WriteLine("exiting function of derived class");  
      Console::WriteLine("=======================");  
   }  
};  
  
int main() {  
   Public_Class ^ a = gcnew Public_Class;  
   MyClass ^ b = gcnew MyClass;  
   a->Public_Function();  
  
   // call protected functions  
   b->Test();  
  
   // can't be called outside the assembly  
   // a->Private_Function();  
   // a->Internal_Function();     
   // a->Protected_Private_Function();  
   // a->Private_Protected_Function();  
}  
```  
  
 **Output**  
  
```Output  
in Public_Function  
=======================  
in function of derived class  
in Protected_Function  
in Protected_Public_Function  
in Public_Protected_Function  
exiting function of derived class  
=======================  
```  
  
##  <a name="BKMK_Public_and_private_native_classes"></a>Veřejné a privátní nativních tříd  
 Nativní typ lze odkazovat z spravovaného typu.  Například funkce v spravovaného typu, může trvat parametr, jehož typ je nativní struktury.  Pokud jsou veřejné v sestavení spravovaného typu a funkce, pak nativní typ musí být také veřejné.  
  
```  
  
// native type  
public struct N {  
   N(){}  
   int i;  
};  
```  
  
 Dále vytvořte souboru zdrojového kódu, který využívá nativní typ:  
  
```  
  
// compile with: /clr /LD  
#include "mcppv2_ref_class3.h"  
// public managed type  
public ref struct R {  
   // public function that takes a native type  
   void f(N nn) {}  
};  
```  
  
 Nyní kompilace klienta:  
  
```  
  
// compile with: /clr  
#using "mcppv2_ref_class3.dll"  
  
#include "mcppv2_ref_class3.h"  
  
int main() {  
   R ^r = gcnew R;  
   N n;  
   r->f(n);  
}  
```  
  
##  <a name="BKMK_Static_constructors"></a>Statické konstruktory  
 Typ CLR – například třídě nebo struktuře – může mít statický konstruktor, který slouží k inicializaci členy statických dat.  Statický konstruktor je volána alespoň jednou a je volána před všechny statický člen typu přistupuje poprvé.  
  
 Konstruktoru instance je spouštěn vždy po statického konstruktoru.  
  
 Kompilátor nelze vložené volání konstruktoru, pokud třída má statického konstruktoru.  Kompilátor nelze vložené volat jakékoli funkce člen, pokud třída je typ hodnoty, má statického konstruktoru a nemá konstruktoru instance.  Modulu CLR může vložené volání, ale nemůže kompilátoru.  
  
 Definujte statického konstruktoru jako funkce privátního člena, protože měl by být volána pouze pomocí modulu CLR.  
  
 Další informace o statické konstruktory najdete v tématu [postupy: definice a používání statického konstruktoru (C + +/ CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .  
  
```  
  
// compile with: /clr  
using namespace System;  
  
ref class MyClass {  
private:  
   static int i = 0;  
  
   static MyClass() {  
      Console::WriteLine("in static constructor");  
      i = 9;  
   }  
  
public:  
   static void Test() {  
      i++;  
      Console::WriteLine(i);  
   }  
};  
  
int main() {  
   MyClass::Test();  
   MyClass::Test();  
}  
```  
  
 **Output**  
  
```Output  
in static constructor  
10  
11  
```  
  
##  <a name="BKMK_Semantics_of_the_this_pointer"></a>Sémantika této ukazatele  
 Pokud používáte Visual C++ pro definování typů, `this` ukazatel v typu odkazu je typu "popisovač". `this` Ukazatel v typ hodnoty je typu "vnitřní ukazatel".  
  
 Tyto různé sémantiku `this` ukazatel může způsobit neočekávané chování při volání výchozí indexer. Další příklad ukazuje způsob správný přístup k výchozí indexeru v typu ref a typ hodnoty.  
  
 Další informace naleznete v tématu  
  
-   [Operátor popisovače objektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)  
  
-   [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)  
  
```  
  
// compile with: /clr  
using namespace System;  
  
ref struct A {  
   property Double default[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
  
   A() {  
      // accessing default indexer  
      Console::WriteLine("{0}", this[3.3]);  
   }  
};  
  
value struct B {  
   property Double default[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
   void Test() {  
      // accessing default indexer  
      Console::WriteLine("{0}", this->default[3.3]);  
   }  
};  
  
int main() {  
   A ^ mya = gcnew A();  
   B ^ myb = gcnew B();  
   myb->Test();  
}  
```  
  
 **Output**  
  
```Output  
10.89  
10.89  
```  
  
##  <a name="BKMK_Hide_by_signature_functions"></a>Funkce skrytí podle podpisu  
 V jazyce C++ standardní funkce v základní třídě je skrytý na základě funkci, která má stejný název v odvozené třídě, i v případě, že funkce odvozené třídy nemá stejný počet nebo druh parametry. Tento proces se označuje jako *skrýt podle názvu* sémantiku. V typu odkazu funkce v základní třídě lze pouze skrýt funkcí v odvozené třídě Pokud název a seznam parametrů jsou stejné. To se označuje jako *skrytí podle podpisu* sémantiku.  
  
 Třídy se považuje za třídu skrytí podle podpisu, pokud všechny funkce jsou označené v metadatech jako `hidebysig`. Ve výchozím nastavení jsou všechny třídy, které se vytvořily pod **/CLR** mít `hidebysig` funkce. Pokud má třídu `hidebysig` funkce, kompilátor není skrýt funkce tak, že název v žádné přímé základní třídy, ale pokud kompilátor zaznamená skrýt podle názvu třídy v řetězce dědičnosti, pokračuje daná chování skrýt podle názvu.  
  
 V části skrytí podle podpisu sémantiku při volání funkce na objekt, kompilátor identifikuje nejvíce odvozené třídy, která obsahuje funkce, která se může stát odpovědí volání funkce. Pokud je třída, která se může stát odpovědí volání jenom jednu funkci, kompilátor volání této funkce. Pokud je třída, která se může stát odpovědí volání více než jednu funkci, používá kompilátoru přetížení pravidel řešení určit funkce, které má být volána. Další informace o pravidlech přetížení, najdete v části [přetížení funkcí](../cpp/function-overloading.md).  
  
 Pro danou funkci volání funkce v základní třídě pravděpodobně podpis, která usnadňuje mírně lepší shodu než funkce v odvozené třídě. Pokud funkce byla explicitně volána objektu odvozené třídy, se nazývá funkce v odvozené třídě.  
  
 Vzhledem k tomu, že návratová hodnota není považovány za součást podpis funkce, funkce základní třídy je skrytý Pokud má stejný název a používá stejný počet a typ argumenty jako funkce odvozené třídy, i když se liší v typ vrácené hodnoty.  
  
 Následující příklad ukazuje, že není funkcí v odvozené třídě skrytý funkce v základní třídě.  
  
```  
  
// compile with: /clr  
using namespace System;  
ref struct Base {  
   void Test() {   
      Console::WriteLine("Base::Test");   
   }  
};  
  
ref struct Derived : public Base {  
   void Test(int i) {   
      Console::WriteLine("Derived::Test");   
   }  
};  
  
int main() {  
   Derived ^ t = gcnew Derived;  
   // Test() in the base class will not be hidden  
   t->Test();  
}  
```  
  
 **Output**  
  
```Output  
Base::Test  
```  
  
 Další příklad ukazuje, že Visual C++ compiler volá funkci nejvíce odvozené třídy – i když převod je vyžadováno tak, aby odpovídaly jeden nebo více parametrů – a není v základní třídu, která představuje lepší shodu pro volání funkce volání funkce.  
  
```  
  
// compile with: /clr  
using namespace System;  
ref struct Base {  
   void Test2(Single d) {   
      Console::WriteLine("Base::Test2");   
   }  
};  
  
ref struct Derived : public Base {  
   void Test2(Double f) {   
      Console::WriteLine("Derived::Test2");   
   }  
};  
  
int main() {  
   Derived ^ t = gcnew Derived;  
   // Base::Test2 is a better match, but the compiler  
   // calls a function in the derived class if possible  
   t->Test2(3.14f);  
}  
```  
  
 **Output**  
  
```Output  
Derived::Test2  
```  
  
 Následující příklad ukazuje, že je možné skrýt funkci i v případě, že se stejným podpisem jako odvozené třídy základní třídy.  
  
```  
  
// compile with: /clr  
using namespace System;  
ref struct Base {  
   int Test4() {   
      Console::WriteLine("Base::Test4");   
      return 9;   
   }  
};  
  
ref struct Derived : public Base {  
   char Test4() {   
      Console::WriteLine("Derived::Test4");   
      return 'a';   
   }  
};  
  
int main() {  
   Derived ^ t = gcnew Derived;  
  
   // Base::Test4 is hidden  
   int i = t->Test4();  
   Console::WriteLine(i);  
}  
```  
  
 **Output**  
  
```Output  
Derived::Test4  
97  
```  
  
##  <a name="BKMK_Copy_constructors"></a>Kopírovací konstruktory  
 Standardní C++ říká, že kopírovacího konstruktoru je volána, když je přesunout objekt, tak, aby objekt je vytvořen a zničen v stejnou adresu.  
  
 Ale když **/CLR** slouží ke kompilaci a funkce, který se zkompiluje do MSIL volání nativní funkce kde nativních tříd – nebo má více než jeden – je předaná hodnota a kde nativních tříd má kopírovacího konstruktoru a/nebo destruktor, žádná kopie volání konstruktoru a objekt zničen na jinou adresu než kdy byla vytvořena. Pokud třída má ukazatel do sebe, nebo pokud kód ke sledování objektů pomocí adresy to může způsobit problémy.  
  
 Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 Následující příklad ukazuje, když se Binder negeneruje kopírovacího konstruktoru.  
  
```  
  
// compile with: /clr  
#include<stdio.h>  
  
struct S {  
   int i;  
   static int n;  
  
   S() : i(n++) {   
      printf_s("S object %d being constructed, this=%p\n", i, this);   
   }  
  
   S(S const& rhs) : i(n++) {   
      printf_s("S object %d being copy constructed from S object "  
               "%d, this=%p\n", i, rhs.i, this);   
   }  
  
   ~S() {  
      printf_s("S object %d being destroyed, this=%p\n", i, this);   
   }  
};  
  
int S::n = 0;  
  
#pragma managed(push,off)  
void f(S s1, S s2) {  
   printf_s("in function f\n");  
}  
#pragma managed(pop)  
  
int main() {  
   S s;  
   S t;  
   f(s,t);  
}  
```  
  
 **Output**  
  
```Output  
S object 0 being constructed, this=0018F378  
S object 1 being constructed, this=0018F37C  
S object 2 being copy constructed from S object 1, this=0018F380  
S object 3 being copy constructed from S object 0, this=0018F384  
S object 4 being copy constructed from S object 2, this=0018F2E4  
S object 2 being destroyed, this=0018F380  
S object 5 being copy constructed from S object 3, this=0018F2E0  
S object 3 being destroyed, this=0018F384  
in function f  
S object 5 being destroyed, this=0018F2E0  
S object 4 being destroyed, this=0018F2E4  
S object 1 being destroyed, this=0018F37C  
S object 0 being destroyed, this=0018F378  
```  
  
##  <a name="BKMK_Destructors_and_finalizers"></a>Destruktory a finalizační metody  
 Destruktory v typu odkazu čištění, deterministická prostředků. Finalizační metody vyčištění nespravované prostředky a lze volat nepodmíněně destruktoru nebo nedeterministicky modulem garbage collector. Informace o destruktorech v standardní C++ najdete v tématu [destruktory](../cpp/destructors-cpp.md).  
  
```  
class classname {  
   ~classname() {}   // destructor  
   ! classname() {}   // finalizer  
};  
```  
  
 Chování destruktory v třídě spravované Visual C++ se liší od spravovaných rozšíření jazyka C++. Další informace o této změně najdete v tématu [změny v sémantice](../dotnet/changes-in-destructor-semantics.md).  
  
 Uvolňování paměti CLR Odstraní nepoužívané spravované objekty a uvolní jejich paměti, když už jsou povinné. Typ však může používat prostředky, které má systém uvolňování nebude vědět, jak k uvolnění. Tyto prostředky se označují jako nespravované prostředky (nativní souboru zpracuje, například). Doporučujeme, abyste uvolnění všechny nespravované prostředky v finalizační metodu. Protože spravované prostředky vydávají nedeterministicky modulem garbage collector, není bezpečné odkazovat na spravované prostředky v finalizační metody vzhledem k tomu, že je možné, že uvolňování má již vyčistit spravované prostředku.  
  
 Finalizační metodu Visual C++ není stejný jako <xref:System.Object.Finalize%2A> metoda. (CLR dokumentace používá finalizační metodu a <xref:System.Object.Finalize%2A> metoda jako synonyma). <xref:System.Object.Finalize%2A> Metoda je volána modulem garbage collector, které vyvolá každý finalizační metodu v řetězu dědičnosti třídy. Na rozdíl od destruktory Visual C++ finalizační metodu odvozené třídy volání nezpůsobí kompilátoru volat finalizační metodu v všechny základní třídy.  
  
 Protože Visual C++ compiler podporuje deterministickou verzi prostředky, nepokoušejte implementovat <xref:System.IDisposable.Dispose%2A> nebo <xref:System.Object.Finalize%2A> metody. Pokud jste obeznámeni s těmito metodami, zde je však jak finalizační metodu Visual C++ a destruktor, který volá finalizační metodu mapovány <xref:System.IDisposable.Dispose%2A> vzoru:  
  
```  
// Visual C++ code  
ref class T {  
   ~T() { this->!T(); }   // destructor calls finalizer  
   !T() {}   // finalizer  
};  
  
// equivalent to the Dispose pattern  
void Dispose(bool disposing) {  
   if (disposing) {  
      ~T();  
   } else {  
      !T();  
   }  
}  
```  
  
 Spravovaný typ mohou používat také spravované prostředky, které si přejete deterministicky a, není zůstat uvolňování k uvolnění nedeterministicky v určitém okamžiku po objekt se už nevyžaduje. Deterministické verzi prostředky může výrazně zlepšit výkon.  
  
 Visual C++ compiler umožňuje definici destruktor nepodmíněně vyčistěte objekty. Pomocí destruktoru uvolní všechny prostředky, které chcete uvolnit nepodmíněně.  Finalizační metody je k dispozici, kontaktujte z destruktor, chcete-li zabránit zdvojení kódu.  
  
```  
  
// compile with: /clr /c  
ref struct A {  
   // destructor cleans up all resources  
   ~A() {  
      // clean up code to release managed resource  
      // ...  
      // to avoid code duplication,   
      // call finalizer to release unmanaged resources  
      this->!A();  
   }  
  
   // finalizer cleans up unmanaged resources  
   // destructor or garbage collector will  
   // clean up managed resources  
   !A() {  
      // clean up code to release unmanaged resources  
      // ...  
   }  
};  
```  
  
 Pokud kód, který využívá vašeho typu nevyvolá destruktoru, bude systém uvolňování nakonec uvolní všechny spravované prostředky.  
  
 Přítomnost destruktor neznamená přítomnost finalizační metody. Však přítomnost finalizační metody znamená, že jste musí definovat destruktor a z této destruktor zavolat finalizační metodu. To umožňuje deterministickou verzi nespravovaných prostředků.  
  
 Volání destruktoru potlačí – pomocí <xref:System.GC.SuppressFinalize%2A>– finalizace objektu. Pokud není volána destruktoru, finalizační metodu vašeho typu nakonec volat modulem garbage collector.  
  
 Nepodmíněně vymazání tohoto objektu prostředků pomocí volání destruktoru může zlepšit výkon ve srovnání s umožníte CLR nedeterministicky dokončit objektu.  
  
 Kód, který má napsané v jazyce Visual C++ a zkompilovat pomocí **/CLR** spouští destruktor typ, pokud:  
  
-   Objekt, který je vytvořen pomocí sémantika zásobníku ocitne mimo rozsah. Další informace najdete v tématu [C++ – sémantika zásobníku pro odkazové typy](../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
-   Při vytváření objektu je vyvolána výjimka.  
  
-   Objekt je člena v objektu, jehož destruktor běží.  
  
-   Volání [odstranit](../cpp/delete-operator-cpp.md) operátor na popisovač ([operátor popisovače objektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)).  
  
-   Explicitní volání destruktoru.  
  
 Pokud váš typ spotřebovává klientem, který je napsána v jiném jazyce, destruktoru následujícím způsobem:  
  
-   Pro volání na <xref:System.IDisposable.Dispose%2A>.  
  
-   Na volání `Dispose(void)` na typu.  
  
-   Pokud typ přejde mimo rozsah v jazyce C# `using` příkaz.  
  
 Pokud vytvoříte objekt typu odkaz na spravovaná halda (ne pomocí sémantika zásobníku pro odkazové typy), použijte [try-finally –](../cpp/try-finally-statement.md) syntaxe zajistit, že výjimku nezabrání destruktoru spuštění.  
  
```  
  
// compile with: /clr  
ref struct A {  
   ~A() {}  
};  
  
int main() {  
   A ^ MyA = gcnew A;  
   try {  
      // use MyA  
   }  
   finally {  
      delete MyA;  
   }  
}  
```  
  
 Pokud má váš typ destruktor, kompilátor vygeneruje `Dispose` metodu, která implementuje <xref:System.IDisposable>. Pokud typ, který je napsaný v jazyce Visual C++ a má destruktor, který je používán z jiný jazyk, volání `IDisposable::Dispose` daný typ způsobí, že destruktor typu k volání. Když je typ zpracován z klienta Visual C++, nelze volat přímo `Dispose`; místo toho volání destruktoru pomocí `delete` operátor.  
  
 Pokud má váš typ finalizační metody, kompilátor vygeneruje `Finalize(void)` metoda, která přepisuje <xref:System.Object.Finalize%2A>.  
  
 Pokud typ má finalizační metody nebo destruktor, kompilátor vygeneruje `Dispose(bool)` metoda, podle vzoru návrhu. (Podrobnosti naleznete v tématu [Dispose vzor](/dotnet/standard/design-guidelines/dispose-pattern)). Nelze explicitně vytvářet nebo volání `Dispose(bool)` v jazyce Visual C++.  
  
 Pokud typ má základní třídu, která vyhovuje vzoru návrhu, se nazývají destruktory pro všechny základní třídy při volání destruktoru pro odvozené třídy. (Pokud váš typ je napsán v jazyce Visual C++, kompilátor zajistí, že vaše typy implementovat tohoto vzoru.) Jinými slovy, destruktoru objektu referenční třídy řetězí jeho základů a členů podle specifikace C++ standard – první třídy destruktor je spustit a pak destruktory pro její členy obráceným pořadí, ve kterém byly sestavený, a nakonec destruktory pro jeho základních tříd obráceným pořadí, ve kterém byly zkonstruovat.  
  
 Destruktory a finalizační metody nejsou povoleny uvnitř typy hodnot nebo rozhraní.  
  
 Finalizační metody pouze nelze definovat ani deklarované v odkazového typu. Finalizační metody jako konstruktor a destruktor, nemá žádný návratový typ.  
  
 Po spuštění finalizační metodu objektu finalizační metody v všechny základní třídy se také nazývají, počínaje nejméně odvozeného typu. Finalizační metody pro datové členy nejsou zřetězené automaticky podle finalizační metodu třídy.  
  
 Pokud finalizační metody odstraní nativní ukazatel v spravovaného typu, je třeba zajistit, že nejsou shromážděna předčasně odkazy nebo prostřednictvím nativní ukazatel; volání destruktoru na spravovaný typ místo použití <xref:System.GC.KeepAlive%2A>.  
  
 Při kompilaci můžete zjistit, zda má finalizační metody nebo destruktor typu. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 Další příklad ukazuje dva typy, ten, který má nespravované prostředky a jeden, který se má spravovat prostředky, které jsou vydané nepodmíněně.  
  
```  
  
// compile with: /clr  
#include <vcclr.h>  
#include <stdio.h>  
using namespace System;  
using namespace System::IO;  
  
ref class SystemFileWriter {  
   FileStream ^ file;  
   array<Byte> ^ arr;  
   int bufLen;  
  
public:  
   SystemFileWriter(String ^ name) : file(File::Open(name, FileMode::Append)),   
                                     arr(gcnew array<Byte>(1024)) {}  
  
   void Flush() {  
      file->Write(arr, 0, bufLen);  
      bufLen = 0;  
   }  
  
   ~SystemFileWriter() {  
      Flush();  
      delete file;  
   }  
};  
  
ref class CRTFileWriter {  
   FILE * file;  
   array<Byte> ^ arr;  
   int bufLen;  
  
   static FILE * getFile(String ^ n) {  
      pin_ptr<const wchar_t> name = PtrToStringChars(n);  
      FILE * ret = 0;  
      _wfopen_s(&ret, name, L"ab");  
      return ret;  
   }  
  
public:  
   CRTFileWriter(String ^ name) : file(getFile(name)), arr(gcnew array<Byte>(1024) ) {}  
  
   void Flush() {  
      pin_ptr<Byte> buf = &arr[0];  
      fwrite(buf, 1, bufLen, file);  
      bufLen = 0;  
   }  
  
   ~CRTFileWriter() {  
      this->!CRTFileWriter();  
   }  
  
   !CRTFileWriter() {  
      Flush();  
      fclose(file);  
   }  
};  
  
int main() {  
   SystemFileWriter w("systest.txt");  
   CRTFileWriter ^ w2 = gcnew CRTFileWriter("crttest.txt");  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)