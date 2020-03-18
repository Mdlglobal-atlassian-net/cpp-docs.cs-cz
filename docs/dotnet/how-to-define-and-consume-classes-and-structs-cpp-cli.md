---
title: 'Postupy: Definice a používání tříd a struktur (C++/CLI)'
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 5fe7d6876b094c84fe3d4cdbba417106edcca528
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418291"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Postupy: Definice a používání tříd a struktur (C++/CLI)

Tento článek ukazuje, jak definovat a využívat uživatelsky definované typy odkazů a typy hodnot v C++/CLI.

##  <a name="BKMK_Contents"></a>Obsah

[Vytváření instancí objektů](#BKMK_Object_instantiation)

[Implicitně abstraktní třídy](#BKMK_Implicitly_abstract_classes)

[Viditelnost typu](#BKMK_Type_visibility)

[Viditelnost členů](#BKMK_Member_visibility)

[Veřejné a soukromé nativní třídy](#BKMK_Public_and_private_native_classes)

[Statické konstruktory](#BKMK_Static_constructors)

[Sémantika tohoto ukazatele](#BKMK_Semantics_of_the_this_pointer)

[Funkce skrývání podle signatury](#BKMK_Hide_by_signature_functions)

[Kopírovací konstruktory](#BKMK_Copy_constructors)

[Destruktory a finalizační metody](#BKMK_Destructors_and_finalizers)

##  <a name="BKMK_Object_instantiation"></a>Vytváření instancí objektů

Typy odkazů (ref) lze vytvořit pouze na spravované haldě, nikoli v zásobníku nebo v nativní haldě. Můžete vytvořit instanci hodnotových typů v zásobníku nebo spravované haldě.

```cpp
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

Instance *implicitně abstraktní třídy* se nedá vytvořit. Třída je implicitně abstraktní, pokud základní typ třídy je rozhraní a třída neimplementuje všechny členské funkce rozhraní.

Pokud nemůžete sestavovat objekty ze třídy, která je odvozena z rozhraní, důvodem může být to, že je třída implicitně abstraktní. Další informace o abstraktních třídách naleznete v tématu [abstract](../extensions/abstract-cpp-component-extensions.md).

Následující příklad kódu ukazuje, že nelze vytvořit instanci `MyClass` třídy, protože `MyClass::func2` funkce není implementována. Chcete-li povolit příklad kompilace, odkomentujte `MyClass::func2`.

```cpp
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

##  <a name="BKMK_Type_visibility"></a>Viditelnost typu

Můžete řídit viditelnost typů modulu CLR (Common Language Runtime), takže pokud je odkazováno na sestavení, mohou být typy v sestavení viditelné nebo nejsou viditelné mimo sestavení.

`public` označuje, že typ je viditelný pro jakýkoliv zdrojový soubor, který obsahuje direktivu `#using` pro sestavení, které obsahuje daný typ.  `private` označuje, že typ není viditelný pro zdrojové soubory, které obsahují direktivu `#using` pro sestavení, které obsahuje daný typ. Soukromé typy jsou však viditelné v rámci stejného sestavení. Ve výchozím nastavení je viditelnost pro třídu `private`.

Ve výchozím nastavení před verzí sady Visual Studio 2005 měly nativní typy veřejné přístupnost mimo sestavení. Povolit [Upozornění kompilátoru (úroveň 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) , které vám pomůžou zjistit, kde se nesprávně používají privátní nativní typy. Použijte direktivu pragma [make_public](../preprocessor/make-public.md) pro udělení veřejné dostupnosti nativnímu typu v souboru zdrojového kódu, který nelze upravit.

Další informace najdete v tématu [direktiva #using](../preprocessor/hash-using-directive-cpp.md).

Následující příklad ukazuje, jak deklarovat typy a zadat jejich přístupnost a pak přistupovat k těmto typům uvnitř sestavení. Samozřejmě, pokud je odkazováno na sestavení, které obsahuje soukromé typy pomocí `#using`, jsou viditelné pouze veřejné typy v sestavení.

```cpp
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

**Výstup**

```Output
in Public_Class
in Private_Class
in Private_Class_2
```

Nyní přepište předchozí vzorek tak, aby byl sestaven jako knihovna DLL.

```cpp
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

Další příklad ukazuje, jak přistupovat k typům mimo sestavení. V této ukázce klient používá komponentu, která je vytvořená v předchozí ukázce.

```cpp
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

**Výstup**

```Output
in Public_Class
```

##  <a name="BKMK_Member_visibility"></a>Viditelnost členů

Můžete nastavit přístup k členovi veřejné třídy v rámci stejného sestavení, které je odlišné od přístupu k němu mimo sestavení, pomocí párů specifikátorů přístupu `public`, `protected`a `private`

Tato tabulka shrnuje účinek různých specifikátorů přístupu:

|Specifikátor|Účinek|
|---------------|------------|
|public|Člen je přístupný v rámci sestavení a mimo něj.  Další informace najdete v tématu [veřejné](../cpp/public-cpp.md) .|
|private|Člen není přístupný, ani uvnitř sestavení ani vně něj.  Další informace najdete v tématu [soukromé](../cpp/private-cpp.md) .|
|protected|Člen je přístupný uvnitř a vně sestavení, ale pouze pro odvozené typy.  Další informace najdete v části [chráněno](../cpp/protected-cpp.md) .|
|internal|Člen je veřejný v rámci sestavení, ale soukromý mimo sestavení.  `internal` je klíčové slovo závislé na kontextu.  Další informace najdete v tématu [Kontextově závislá klíčová slova](../extensions/context-sensitive-keywords-cpp-component-extensions.md).|
|Veřejná chráněná nebo chráněná veřejný|Člen je veřejný v rámci sestavení, ale je chráněn mimo sestavení.|
|soukromá chráněná nebo chráněná privátní|Člen je chráněn v rámci sestavení, ale soukromý mimo sestavení.|

Následující příklad znázorňuje veřejný typ, který má členy deklarované s různými přístupnosti a pak zobrazuje přístup těchto členů zevnitř sestavení.

```cpp
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

**Výstup**

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

Nyní sestavíme předchozí vzorek jako knihovnu DLL.

```cpp
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

Následující ukázka používá komponentu, která je vytvořena v předchozí ukázce, a ukazuje, jak získat přístup ke členům mimo sestavení.

```cpp
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

**Výstup**

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

##  <a name="BKMK_Public_and_private_native_classes"></a>Veřejné a soukromé nativní třídy

Na nativní typ se dá odkazovat ze spravovaného typu.  Například funkce ve spravovaném typu může převzít parametr, jehož typ je nativní struktura.  Pokud je spravovaný typ a funkce veřejné v sestavení, musí být nativní typ také veřejný.

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

Dále vytvořte soubor zdrojového kódu, který spotřebovává nativní typ:

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

Nyní zkompilujte klienta:

```cpp
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

Typ CLR, například třída nebo struktura – může mít statický konstruktor, který lze použít k inicializaci statických datových členů.  Statický konstruktor je volán nejvíce jednou a je volán před prvním přistupem ke statickému členu typu.

Konstruktor instance se vždy spouští po statickém konstruktoru.

Kompilátor nemůže vložit volání do konstruktoru, pokud má třída statický konstruktor.  Kompilátor nemůže vložit volání do jakékoli členské funkce, je-li třída typem hodnoty, má statický konstruktor a nemá konstruktor instance.  CLR může vložit volání, ale kompilátor nemůže.

Definujte statický konstruktor jako soukromou členskou funkci, protože je určena pro volání pouze CLR.

Další informace o statických konstruktorech naleznete v tématu [How to: define a static interfaceC++(/CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .

```cpp
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

**Výstup**

```Output
in static constructor
10
11
```

##  <a name="BKMK_Semantics_of_the_this_pointer"></a>Sémantika tohoto ukazatele

Při použití vizuálu C++ k definování typů je ukazatel `this` v typu odkazu typu Handle. Ukazatel `this` v hodnotovém typu je typu "vnitřní ukazatel".

Tato odlišná sémantika `this` ukazatele může způsobit neočekávané chování při volání výchozího indexeru. Následující příklad ukazuje správný způsob, jak získat přístup k výchozímu indexeru v typu ref a v hodnotovém typu.

Další informace najdete v tématu

- [Operátor popisovače objektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](../extensions/interior-ptr-cpp-cli.md)

```cpp
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

**Výstup**

```Output
10.89
10.89
```

##  <a name="BKMK_Hide_by_signature_functions"></a>Funkce skrývání podle signatury

Ve standard C++je funkce v základní třídě skrytá funkcí, která má stejný název v odvozené třídě, i když funkce odvozené třídy nemá stejný počet nebo druh parametrů. To se označuje jako sémantika *skrytí podle názvu* . V typu odkazu může být funkce v základní třídě skrytá pouze funkcí v odvozené třídě, pokud je název i seznam parametrů stejný. To se označuje jako sémantika *skrytého podle podpisu* .

Třída je považována za třídu skrytou po podpisu, pokud jsou všechny její funkce označeny v metadatech jako `hidebysig`. Ve výchozím nastavení všechny třídy, které jsou vytvořeny v rámci **/CLR** , mají `hidebysig` funkce. Pokud má třída `hidebysig` Functions, kompilátor neskrývá funkce podle názvu v žádné přímé základní třídě, ale pokud kompilátor nalezne v řetězu dědičnosti třídu po názvu, pokračuje v tom, že chování funkce skrýt podle názvu pokračuje.

Pokud je funkce volána pro objekt v rámci sémantiky skryté podle signatury, kompilátor identifikuje největší odvozenou třídu, která obsahuje funkci, která by mohla naplnit volání funkce. Pokud existuje pouze jedna funkce ve třídě, která by mohla naplnit volání, volá kompilátor tuto funkci. Pokud existuje více než jedna funkce ve třídě, která by mohla naplnit volání, kompilátor používá pravidla řešení přetížení k určení, která funkce se má volat. Další informace o pravidlech přetížení naleznete v tématu přetížení [funkce](../cpp/function-overloading.md).

Pro dané volání funkce může mít funkce v základní třídě signaturu, která je mírně lepší, než funkce v odvozené třídě. Nicméně, pokud byla funkce explicitně volána pro objekt odvozené třídy, je volána funkce v odvozené třídě.

Vzhledem k tomu, že návratová hodnota není považována za součást signatury funkce, je funkce základní třídy skrytá, pokud má stejný název a má stejný počet a druh argumentů jako funkce odvozené třídy, a to i v případě, že se liší od typu návratové hodnoty.

Následující příklad ukazuje, že funkce v základní třídě není skrytá funkcí v odvozené třídě.

```cpp
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

**Výstup**

```Output
Base::Test
```

Následující příklad ukazuje, že kompilátor společnosti C++ Microsoft volá funkci v nejvíce odvozené třídě – i v případě, že je vyžadován převod pro shodu s jedním nebo více parametry – a nevolá funkci v základní třídě, která je lepší shodou pro volání funkce.

```cpp
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

**Výstup**

```Output
Derived::Test2
```

Následující příklad ukazuje, že je možné skrýt funkci i v případě, že základní třída má stejný podpis jako odvozená třída.

```cpp
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

**Výstup**

```Output
Derived::Test4
97
```

##  <a name="BKMK_Copy_constructors"></a>Kopírovací konstruktory

C++ Standard říká, že kopírovací konstruktor je volán při přesunu objektu, například vytvoření a zničení objektu na stejné adrese.

Nicméně, pokud je funkce **/CLR** použita ke kompilaci a funkce, která je zkompilována do jazyka MSIL, volá nativní funkci, kde je nativní třída (nebo více než jedna) předána hodnotou a kde nativní třída obsahuje kopírovací konstruktor nebo destruktor, není volán žádný kopírovací konstruktor a objekt je zničen na jiné adrese, než kde byl vytvořen. To může způsobit problémy, pokud má třída ukazatel na sebe samu, nebo pokud kód sleduje objekty podle adresy.

Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

Následující příklad ukazuje, kdy není vytvořen kopírovací konstruktor.

```cpp
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

**Výstup**

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

Destruktory v typu odkazu provádějí deterministické vyčištění prostředků. Finalizační metody čistí nespravované prostředky a mohou být volány deterministickým destruktorem nebo nedeterministickým systémem uvolňování paměti. Informace o destruktorech ve standardu C++naleznete v tématu [destruktory](../cpp/destructors-cpp.md).

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Chování destruktorů ve spravované třídě vizuálu C++ se liší od spravovaných rozšíření pro. C++ Další informace o této změně najdete v tématu [změny sémantiky destruktoru](../dotnet/changes-in-destructor-semantics.md).

Systém uvolňování paměti CLR Odstraní nepoužívané spravované objekty a uvolní jejich paměť, pokud již nejsou vyžadovány. Typ však může používat prostředky, které systém uvolňování paměti neví, jak vydávat. Tyto prostředky se označují jako nespravované prostředky (například nativní obslužné rutiny souborů). Doporučujeme uvolnit všechny nespravované prostředky v finalizační metodě. Vzhledem k tomu, že spravované prostředky jsou uvolněny nedeterministické systémem uvolňování paměti, není bezpečné odkazovat na spravované prostředky v finalizační službě, protože je možné, že systém uvolňování paměti již vyčistil tento spravovaný prostředek.

Nevizuální C++ finalizační metoda není shodná s metodou <xref:System.Object.Finalize%2A>. (Dokumentace CLR používá finalizační metodu a <xref:System.Object.Finalize%2A> metody jako synonyma). Metoda <xref:System.Object.Finalize%2A> je volána systémem uvolňování paměti, který vyvolá každý finalizační metodu v řetězci dědičnosti třídy. Na rozdíl od C++ vizuálních destruktorů, volání finalizační metody odvozené třídy nezpůsobí, že kompilátor vyvolá finalizační metodu ve všech základních třídách.

Vzhledem k tomu C++ , že kompilátor Microsoft podporuje deterministické vydání prostředků, nepokoušejte se implementovat metody <xref:System.IDisposable.Dispose%2A> nebo <xref:System.Object.Finalize%2A>. Pokud jste však obeznámeni s těmito metodami, tady je postup vizuální C++ finalizační metody a destruktoru, který volá mapu finalizační metody do <xref:System.IDisposable.Dispose%2A>ho vzoru:

```cpp
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

Spravovaný typ může také používat spravované prostředky, které byste chtěli použít k deterministickému vydání, a ne pro uvolňování paměti, aby vydávaly nedeterministické informace v určitém okamžiku, kdy objekt již není požadován. Deterministické vydání prostředků může významně zlepšit výkon.

Kompilátor společnosti C++ Microsoft umožňuje definici destruktoru deterministického vyčištění objektů. Pomocí destruktoru uvolněte všechny prostředky, které chcete deterministické vydávat.  Pokud je přítomen finalizační metoda, zavolejte ji z destruktoru, abyste se vyhnuli duplicitám kódu.

```cpp
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

Pokud kód, který využívá váš typ, nevolá destruktor, uvolňování paměti nakonec uvolní všechny spravované prostředky.

Přítomnost destruktoru neznamená přítomnost finalizační metody. Nicméně přítomnost finalizační metody znamená, že je nutné definovat destruktor a volat finalizační metodu z tohoto destruktoru. Tato informace je k dispozici pro deterministické vydání nespravovaných prostředků.

Volání destruktoru potlačuje – pomocí <xref:System.GC.SuppressFinalize%2A>– finalizace objektu. Pokud není volán destruktor, bude finalizační metoda typu volána systémem uvolňování paměti.

Deterministické vyčištění prostředků objektu voláním destruktoru může zvýšit výkon v porovnání s povolením CLR nedeterministickému dokončení objektu.

Kód, který je napsán v C++ jazyce Visual a kompilován pomocí **/CLR** , spouští destruktor typu, pokud:

- Objekt, který je vytvořen pomocí sémantiky zásobníku, se přechází mimo rozsah. Další informace naleznete v tématu [ C++ sémantika zásobníku pro odkazové typy](../dotnet/cpp-stack-semantics-for-reference-types.md).

- Během konstrukce objektu je vyvolána výjimka.

- Objekt je členem v objektu, jehož destruktor je spuštěn.

- Operátor [Delete](../cpp/delete-operator-cpp.md) zavoláte na popisovač ([popisovač k objektu operátor (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)).

- Explicitně voláte destruktor.

Pokud je váš typ využíván klientem, který je napsán v jiném jazyce, je volán následující destruktor:

- Při volání <xref:System.IDisposable.Dispose%2A>.

- Při volání `Dispose(void)` pro typ.

- Pokud se typ z oboru v příkazu C# `using` nedostane mimo rozsah.

Pokud vytvoříte objekt typu odkazu na spravované haldě (nepoužíváte sémantiku zásobníku pro odkazové typy), použijte syntaxi [try-finally](../cpp/try-finally-statement.md) , abyste zajistili, že výjimka nebrání spuštění destruktoru.

```cpp
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

Pokud má typ destruktor, kompilátor vygeneruje metodu `Dispose`, která implementuje <xref:System.IDisposable>. Pokud typ, který je napsán v jazyce C++ Visual a má destruktor, který je spotřebován z jiného jazyka, volání `IDisposable::Dispose` na tomto typu způsobí volání destruktoru typu. Když je typ spotřebován z vizuálního C++ klienta, nemůžete přímo volat `Dispose`; místo toho zavolejte destruktor pomocí operátoru `delete`.

Pokud má váš typ finalizační metodu, kompilátor vygeneruje metodu `Finalize(void)`, která přepíše <xref:System.Object.Finalize%2A>.

Pokud typ má buď finalizační metodu, nebo destruktor, kompilátor vygeneruje metodu `Dispose(bool)` podle vzoru návrhu. (Informace naleznete v tématu [vzor Dispose](/dotnet/standard/design-guidelines/dispose-pattern)). V vizuálu C++nemůžete explicitně vytvořit nebo volat `Dispose(bool)`.

Pokud má typ základní třídu, která odpovídá vzoru návrhu, jsou volány destruktory pro všechny základní třídy při volání destruktoru pro odvozenou třídu. (Pokud je váš typ napsán ve vizuálu C++, kompilátor zajistí, že vaše typy implementují tento model.) Jinými slovy, destruktor třídy odkazu řetězí ke svým základům a členům, jak je uvedeno ve C++ standardu – nejprve je spuštěn destruktor třídy, potom destruktory pro jeho členy v obráceném pořadí, ve kterém byly vytvořeny, a nakonec destruktory pro své základní třídy v opačném pořadí, ve kterém byly vytvořeny.

Destruktory a finalizační metody nejsou povoleny uvnitř hodnotových typů nebo rozhraní.

Finalizační metodu lze definovat nebo deklarovat pouze v typu odkazu. Jako konstruktor a destruktor nemá finalizační metoda žádný návratový typ.

Po spuštění finalizační metody objektu jsou také volány finalizační metody v jakékoli základní třídě počínaje minimálním odvozeným typem. Finalizační metody pro datové členy nejsou automaticky zřetězeny pomocí finalizační metody třídy.

Pokud finalizační metoda odstraní nativní ukazatel ve spravovaném typu, je nutné zajistit, aby odkazy na nebo prostřednictvím nativního ukazatele nebyly předčasně shromažďovány. místo použití <xref:System.GC.KeepAlive%2A>volejte destruktor na spravovaném typu.

V době kompilace můžete zjistit, zda má typ finalizační metodu nebo destruktor. Další informace naleznete v tématu [Podpora kompilátoru pro typové vlastnosti](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

Následující příklad ukazuje dva typy, jeden s nespravovanými prostředky a jeden, který má spravované prostředky, které jsou deterministické.

```cpp
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

[Třídy a struktury](../extensions/classes-and-structs-cpp-component-extensions.md)<br/>
[Třídy a struktury](../extensions/classes-and-structs-cpp-component-extensions.md)
