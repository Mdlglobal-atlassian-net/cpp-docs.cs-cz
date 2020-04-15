---
title: 'Postupy: Definice a používání tříd a struktur (C++/CLI)'
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 5bec92ce2bd97f11723cdf59c58b7331b39565f2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370186"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Postupy: Definice a používání tříd a struktur (C++/CLI)

Tento článek ukazuje, jak definovat a využívat uživatelem definované typy odkazů a typy hodnot v jazyce C++/CLI.

## <a name="contents"></a><a name="BKMK_Contents"></a>Obsah

[Vytvoření instance objektu](#BKMK_Object_instantiation)

[Implicitně abstraktní třídy](#BKMK_Implicitly_abstract_classes)

[Viditelnost typu](#BKMK_Type_visibility)

[Viditelnost členů](#BKMK_Member_visibility)

[Veřejné a soukromé nativní třídy](#BKMK_Public_and_private_native_classes)

[Statické konstruktory](#BKMK_Static_constructors)

[Sémantika tohoto ukazatele](#BKMK_Semantics_of_the_this_pointer)

[Funkce skrýt podle podpisu](#BKMK_Hide_by_signature_functions)

[Kopírovat konstruktory](#BKMK_Copy_constructors)

[Destruktory a finalizační metody](#BKMK_Destructors_and_finalizers)

## <a name="object-instantiation"></a><a name="BKMK_Object_instantiation"></a>Vytvoření instance objektu

Reference (ref) typy lze pouze instance na spravované haldy, nikoli v zásobníku nebo na nativní haldy. Typy hodnot lze vytvořit instance v zásobníku nebo spravované haldy.

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

## <a name="implicitly-abstract-classes"></a><a name="BKMK_Implicitly_abstract_classes"></a>Implicitně abstraktní třídy

Implicitně *abstraktní třídy* nelze vytvořit instanci. Třída je implicitně abstraktní, pokud je základní typ třídy rozhraní a třída neimplementuje všechny členské funkce rozhraní.

Pokud nejste schopni vytvořit objekty z třídy, která je odvozena z rozhraní, důvodem může být, že třída je implicitně abstraktní. Další informace o abstraktních třídách naleznete [v tématu abstract](../extensions/abstract-cpp-component-extensions.md).

Následující příklad kódu ukazuje, `MyClass` že třídu nelze vytvořit `MyClass::func2` instanci, protože funkce není implementována. Chcete-li povolit kompilování příkladu, odkomentujte . `MyClass::func2`

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

## <a name="type-visibility"></a><a name="BKMK_Type_visibility"></a>Viditelnost typu

Můžete řídit viditelnost běžných typů za běhu jazyka (CLR), takže pokud je odkazováno na sestavení, typy v sestavení mohou být viditelné nebo nejsou viditelné mimo sestavení.

`public`označuje, že typ je viditelný pro `#using` libovolný zdrojový soubor, který obsahuje direktivu pro sestavení, které obsahuje typ.  `private`označuje, že typ není viditelný pro `#using` zdrojové soubory, které obsahují direktivu pro sestavení, které obsahuje typ. Soukromé typy jsou však viditelné ve stejném sestavení. Ve výchozím nastavení je `private`viditelnost třídy .

Ve výchozím nastavení před Visual Studio 2005 nativní typy měly veřejnou přístupnost mimo sestavení. Povolte [upozornění kompilátoru (úroveň 1) C4692,](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) které vám pomohou zjistit, kde se nesprávně používají soukromé nativní typy. Pomocí [make_public](../preprocessor/make-public.md) pragma udělit veřejnou přístupnost nativnímu typu v souboru zdrojového kódu, který nelze upravit.

Další informace naleznete [v #using směrnice](../preprocessor/hash-using-directive-cpp.md).

Následující ukázka ukazuje, jak deklarovat typy a určit jejich usnadnění přístupu a potom přístup k těmto typům uvnitř sestavení. Samozřejmě pokud sestavení, které má soukromé typy `#using`odkazuje pomocí , jsou viditelné pouze veřejné typy v sestavení.

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

Nyní přepíšeme předchozí ukázku tak, aby byla vytvořena jako dll.

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

Další ukázka ukazuje, jak získat přístup k typům mimo sestavení. V této ukázce klient spotřebovává součást, která je postavena v předchozí ukázce.

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

## <a name="member-visibility"></a><a name="BKMK_Member_visibility"></a>Viditelnost členů

Můžete získat přístup k člen veřejné třídy ze stejného sestavení, které se liší od přístupu `public`k `protected`němu mimo sestavení pomocí párů specifikátorů přístupu , a`private`

Tato tabulka shrnuje účinek různých specifikátorů přístupu:

|Specifikátor|Účinek|
|---------------|------------|
|public|Člen je přístupný uvnitř i vně sestavy.  Další informace naleznete na [veřejnosti.](../cpp/public-cpp.md)|
|private|Člen není přístupný, ani uvnitř, ani mimo sestavení.  Další informace naleznete v [soukromém](../cpp/private-cpp.md) sektoru.|
|protected|Člen je přístupný uvnitř i vně sestavení, ale pouze pro odvozené typy.  Další informace naleznete v [tématu chráněné.](../cpp/protected-cpp.md)|
|internal|Člen je veřejný uvnitř sestavení, ale soukromé mimo sestavení.  `internal`je kontextové klíčové slovo.  Další informace naleznete [v tématu Kontextová klíčová slova](../extensions/context-sensitive-keywords-cpp-component-extensions.md).|
|veřejně chráněná nebo chráněná veřejná|Member je veřejné uvnitř sestavení, ale chráněné mimo sestavení.|
|soukromé chráněné nebo chráněné soukromé|Člen je chráněn uvnitř sestavení, ale soukromé mimo sestavení.|

Následující ukázka ukazuje veřejný typ, který má členy, které jsou deklarovány s různými přístupovými vlastnostmi a potom zobrazuje přístup těchto členů z uvnitř sestavení.

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

Nyní vytvoříme předchozí ukázku jako dll.

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

Následující ukázka spotřebovává součást, která je vytvořena v předchozí ukázce, a tím ukazuje, jak získat přístup k členům mimo sestavení.

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

## <a name="public-and-private-native-classes"></a><a name="BKMK_Public_and_private_native_classes"></a>Veřejné a soukromé nativní třídy

Na nativní typ lze odkazovat ze spravovaného typu.  Například funkce ve spravovaném typu může trvat parametr, jehož typ je nativní struktura.  Pokud spravovaný typ a funkce jsou veřejné v sestavení, pak nativní typ musí být také veřejné.

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

## <a name="static-constructors"></a><a name="BKMK_Static_constructors"></a>Statické konstruktory

Typ CLR – například třída nebo struktura – může mít statický konstruktor, který lze použít k inicializaci statických datových členů.  Statický konstruktor je volána maximálně jednou a je volána před všechny statické člen typu je přístupná při prvním.

Instance konstruktor vždy běží po statické konstruktoru.

Kompilátor nemůže vsazovat volání konstruktoru, pokud má třída statický konstruktor.  Kompilátor nemůže vložit volání žádné členské funkce, pokud je třída typ hodnoty, má statický konstruktor a nemá konstruktor instance.  CLR může vsazení volání, ale kompilátor nemůže.

Definujte statický konstruktor jako soukromou členovou funkci, protože je určena pouze clr.

Další informace o statických konstruktorech naleznete v [tématu How to: Define a Interface Static Constructor (C++/CLI).](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

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

## <a name="semantics-of-the-this-pointer"></a><a name="BKMK_Semantics_of_the_this_pointer"></a>Sémantika tohoto ukazatele

Při použití visual c++ definovat typy, `this` ukazatel v typu odkazu je typu "popisovač". Ukazatel `this` v typu hodnoty je typu "vnitřní ukazatel".

Tyto různé sémantiky `this` ukazatele může způsobit neočekávané chování při volání výchozí indexer. Následující příklad ukazuje správný způsob přístupu k výchozí indexer u ref typu a typu hodnoty.

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

## <a name="hide-by-signature-functions"></a><a name="BKMK_Hide_by_signature_functions"></a>Funkce skrýt podle podpisu

Ve standardním jazyce C++ je funkce v základní třídě skryta funkcí, která má stejný název v odvozené třídě, i když funkce odvozené třídy nemá stejný počet nebo druh parametrů. To se označuje jako sémantiku *skrýt podle názvu.* V typu odkazu může být funkce v základní třídě skryta pouze funkcí v odvozené třídě, pokud jsou název i seznam parametrů stejné. Tento stav se označuje jako sémantiku *podle skrytí* podle podpisu.

Třída je považována za skrýt podle podpisu třídy, pokud jsou `hidebysig`všechny jeho funkce označeny v metadatech jako . Ve výchozím nastavení mají všechny třídy, `hidebysig` které jsou vytvořeny pod **/clr,** funkce. Pokud má `hidebysig` třída funkce, kompilátor neskrývá funkce podle názvu v žádné přímé základní třídy, ale pokud kompilátor narazí na skrýt podle názvu třídy v řetězci dědičnosti, pokračuje, že skrýt podle názvu chování.

V části sémantiku skrýt podle podpisu, když je funkce volána na objekt, kompilátor identifikuje nejvíce odvozené třídy, která obsahuje funkci, která by mohla uspokojit volání funkce. Pokud existuje pouze jedna funkce ve třídě, která by mohla uspokojit volání, kompilátor volá tuto funkci. Pokud existuje více než jednu funkci ve třídě, která by mohla uspokojit volání, kompilátor používá pravidla řešení přetížení k určení, které funkce volat. Další informace o přetížení pravidla naleznete v [tématu přetížení funkce](../cpp/function-overloading.md).

Pro dané volání funkce funkce v základní třídě může mít podpis, který umožňuje o něco lepší shodu než funkce v odvozené třídě. Pokud však byla funkce explicitně volána na objekt odvozené třídy, je volána funkce v odvozené třídě.

Vzhledem k tomu, že vrácená hodnota není považována za součást podpisu funkce, funkce základní třídy je skryta, pokud má stejný název a má stejný počet a druh argumentů jako funkce odvozené třídy, i když se liší v typu vrácené hodnoty.

Následující ukázka ukazuje, že funkce v základní třídě není skryta funkcí v odvozené třídě.

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

Další ukázka ukazuje, že kompilátor Microsoft C++ volá funkci v nejvíce odvozené třídě – i v případě, že převod je nutné odpovídat jeden nebo více parametrů – a není volání funkce v základní třídě, která je lepší shoda pro volání funkce.

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

Následující ukázka ukazuje, že je možné skrýt funkci i v případě, že základní třída má stejný podpis jako odvozené třídy.

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

## <a name="copy-constructors"></a><a name="BKMK_Copy_constructors"></a>Kopírovat konstruktory

Standard Jazyka C++ říká, že konstruktor kopie je volána při přesunutí objektu, tak, aby objekt je vytvořen a zničen na stejné adrese.

Však při **/clr** se používá ke kompilaci a funkce, která je zkompilována do MSIL volá nativní funkce, kde nativní třídy – nebo více než jeden – je předán hodnotou a kde nativní třída má konstruktor kopie nebo destruktor, žádná kopie konstruktor je volána a objekt je zničen na jinou adresu, než kde byl vytvořen. To může způsobit problémy, pokud třída má ukazatel do sebe, nebo pokud kód sleduje objekty podle adresy.

Další informace naleznete v tématu [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

Následující ukázka ukazuje, když není generován konstruktor kopie.

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

## <a name="destructors-and-finalizers"></a><a name="BKMK_Destructors_and_finalizers"></a>Destruktory a finalizační metody

Destruktory v typ odkazu provést deterministické vyčištění prostředků. Finalizační metody vyčistit nespravované prostředky a může být volána deterministicky destruktor nebo nedeterministicky systémem uvolňování paměti. Informace o destruktorech ve standardním jazyce C++ naleznete v [tématu Destructors](../cpp/destructors-cpp.md).

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Chování destruktores ve spravované visual c++ třídy se liší od spravovaných rozšíření pro C++. Další informace o této změně naleznete [v tématu Změny sémantiky destruktoru](../dotnet/changes-in-destructor-semantics.md).

Uvolňování CLR odstraní nepoužívané spravované objekty a uvolní jejich paměť, pokud již nejsou vyžadovány. Typ však může používat prostředky, které systém uvolňování paměti neví, jak uvolnit. Tyto prostředky jsou označovány jako nespravované prostředky (například nativní popisovače souborů). Doporučujeme uvolnit všechny nespravované prostředky ve finalizační metodě. Vzhledem k tomu, že spravované prostředky jsou uvolněny nedeterministicky systémem uvolňování paměti, není bezpečné odkazovat na spravované prostředky ve finalizační metodě, protože je možné, že systém uvolňování paměti již tento spravovaný prostředek vyčistil.

Finalizační metoda visual c++ není <xref:System.Object.Finalize%2A> stejná jako metoda. (CLR dokumentace používá finalizační metodu a metodu <xref:System.Object.Finalize%2A> synonymně). Metoda <xref:System.Object.Finalize%2A> je volána systémem uvolňování paměti, který vyvolá každou finalizační metodu v řetězci dědičnosti třídy. Na rozdíl od destruktory Visual C++ volání finalizační metody odvozené třídy nezpůsobí, že kompilátor vyvolá finalizační metodu ve všech základních třídách.

Vzhledem k tomu, že kompilátor Microsoft C++ podporuje <xref:System.IDisposable.Dispose%2A> deterministické uvolnění prostředků, nepokoušejte se implementovat metody nebo. <xref:System.Object.Finalize%2A> Pokud však jste obeznámeni s těmito metodami, tady je způsob finalizační metody Visual C++ <xref:System.IDisposable.Dispose%2A> a destruktoru, která volá mapu finalizační metody do vzoru:

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

Spravovaný typ může také používat spravované prostředky, které byste raději uvolnit deterministicky a neponechat na uvolňování uvolnit nedeterministicky v určitém okamžiku poté, co objekt již není vyžadován. Deterministické uvolnění prostředků může výrazně zlepšit výkon.

Kompilátor Microsoft C++ umožňuje definici destruktoru deterministicky vyčistit objekty. Pomocí destruktoru uvolněte všechny prostředky, které chcete deterministicky uvolnit.  Pokud je k dispozici finalizační metoda, zavolejte z destruktoru, abyste se vyhnuli duplikaci kódu.

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

Pokud kód, který spotřebovává váš typ nevolá destruktor, uvolňování nakonec uvolní všechny spravované prostředky.

Přítomnost destruktoru neznamená přítomnost finalizační metody. Přítomnost finalizační metody však znamená, že je nutné definovat destruktor a volat finalizační metodu z tohoto destruktoru. To umožňuje deterministické uvolnění nespravovaných prostředků.

Volání destruktoru potlačí <xref:System.GC.SuppressFinalize%2A>– pomocí – dokončení objektu. Pokud destruktor není volána, finalizační metoda typu bude nakonec volána systémem uvolňování paměti.

Deterministicky vyčištění prostředků objektu voláním destruktoru může zlepšit výkon ve srovnání s nechat CLR nedeterministicky dokončit objekt.

Kód, který je napsán v jazyce Visual C++ a zkompilován pomocí **/clr** spustí destruktor typu, pokud:

- Objekt, který je vytvořen pomocí sémantiky zásobníku přejde mimo rozsah. Další informace naleznete v [tématu C++ Stack Sémantiku pro typy odkazů](../dotnet/cpp-stack-semantics-for-reference-types.md).

- Během konstrukce objektu je vyvolána výjimka.

- Objekt je členem v objektu, jehož destruktor je spuštěn.

- Operátor [odstranění](../cpp/delete-operator-cpp.md) voláte na popisovači ([Handle to Object Operator (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)).

- Výslovně voláte destruktor.

Pokud je váš typ spotřebovává klient, který je napsán v jiném jazyce, destruktor se nazývá takto:

- Při volání <xref:System.IDisposable.Dispose%2A>do .

- Na volání `Dispose(void)` na typu.

- Pokud typ přejde mimo rozsah `using` v příkazu C#.

Pokud vytvoříte objekt typu odkazu na spravované haldy (nepoužíváte sémantiku zásobníku pro typy odkazů), použijte [syntaxi try-finally,](../cpp/try-finally-statement.md) abyste zajistili, že výjimka nezabrání spuštění destruktoru.

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

Pokud váš typ má destruktor, kompilátor generuje <xref:System.IDisposable>metodu, která implementuje `Dispose` . Pokud typ, který je napsán v jazyce Visual C++ a má destruktor, který je spotřebována z jiného jazyka, volání `IDisposable::Dispose` na tento typ způsobí, že destruktor typu, které mají být volány. Když je typ spotřebován z klienta Visual C++, nelze přímo volat `Dispose`; místo toho volání destruktoru `delete` pomocí operátoru.

Pokud váš typ má finalizační metodu, `Finalize(void)` kompilátor <xref:System.Object.Finalize%2A>generuje metodu, která přepíše .

Pokud má typ finalizační metodu nebo destruktor, `Dispose(bool)` kompilátor vygeneruje metodu podle návrhového vzoru. (Informace naleznete v tématu [Dispose Pattern](/dotnet/standard/design-guidelines/dispose-pattern)). V jazyce Visual `Dispose(bool)` C++ nelze explicitně vytvářet ani volat.

Pokud typ má základní třídu, která odpovídá návrhu vzoru, destruktory pro všechny základní třídy jsou volány při volání destruktoru pro odvozené třídy. (Pokud je váš typ napsán v jazyce Visual C++, kompilátor zajišťuje, že vaše typy implementují tento vzor.) Jinými slovy, destruktor referenční třídy řetězí na své základy a členy, jak je specifikováno standardem C++– nejprve je spuštěn destruktor třídy, potom destruktory pro její členy v opačném pořadí, ve kterém byly vytvořeny, a nakonec destruktory pro jeho základní třídy v opačném pořadí, ve kterém byly vytvořeny.

Destruktory a finalizační metody nejsou povoleny uvnitř typy hodnot nebo rozhraní.

Finalizační metodu lze definovat nebo deklarovat pouze v typu odkazu. Podobně jako konstruktor a destruktor nemá finalizační metoda žádný návratový typ.

Po spuštění finalizační metody objektu finalizační metody v libovolné základní třídy jsou také volány, počínaje nejméně odvozené typu. Finalizační metody pro datové členy nejsou automaticky zřetězeny finalizační inizitou třídy.

Pokud finalizační metoda odstraní nativní ukazatel ve spravovaném typu, je nutné zajistit, aby odkazy na nebo prostřednictvím nativní ukazatel nejsou předčasně shromážděny; volání destruktoru na spravovaný typ namísto použití <xref:System.GC.KeepAlive%2A>.

V době kompilace můžete zjistit, zda typ má finalizační metodu nebo destruktor. Další informace naleznete v [tématu Podpora kompilátoru pro vlastnosti typu](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

Další ukázka zobrazuje dva typy, jeden, který má nespravované prostředky a jeden, který má spravované prostředky, které jsou deterministicky uvolněny.

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
