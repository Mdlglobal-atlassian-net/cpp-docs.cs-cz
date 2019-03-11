---
title: 'Postupy: Definice a používání tříd a struktur (C + +/ CLI)'
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 2c43234ca05c661d8f3d920b1129256a7550a5e2
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751827"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Postupy: Definice a používání tříd a struktur (C + +/ CLI)

Tento článek popisuje, jak definovat a využívat typy odkazů definované uživatelem a typů hodnot v jazyce C + +/ CLI.

##  <a name="BKMK_Contents"></a> Obsah

[Vytvoření instance objektu](#BKMK_Object_instantiation)

[Implicitně abstraktní třídy](#BKMK_Implicitly_abstract_classes)

[Viditelnost typů](#BKMK_Type_visibility)

[Viditelnost členů](#BKMK_Member_visibility)

[Veřejné a soukromé nativních tříd](#BKMK_Public_and_private_native_classes)

[Statické konstruktory](#BKMK_Static_constructors)

[Sémantika tento ukazatel](#BKMK_Semantics_of_the_this_pointer)

[Skrytí podle podpisu funkce](#BKMK_Hide_by_signature_functions)

[Kopírovací konstruktory](#BKMK_Copy_constructors)

[Destruktory a finalizační metody](#BKMK_Destructors_and_finalizers)

##  <a name="BKMK_Object_instantiation"></a> Vytvoření instance objektu

Typy odkazů (referenční) může být vytvořena, pouze na spravované haldě, ne na zásobníku nebo na nativní haldě. Typy hodnot může být vytvořena na zásobníku nebo spravované haldě.

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

##  <a name="BKMK_Implicitly_abstract_classes"></a> Implicitně abstraktní třídy

*Implicitně abstraktní třídy* se nedá vytvořit instance. Třída je implicitně abstraktní, pokud je základní typ třídy, rozhraní a třídy neimplementuje všechny funkce člena rozhraní.

Pokud se nemůžete k vytvoření objektů ze třídy, který je odvozen z rozhraní, důvodem může být, že je implicitně abstraktní třídy. Další informace o abstraktních tříd naleznete v tématu [abstraktní](../windows/abstract-cpp-component-extensions.md).

Následující příklad kódu ukazuje, že `MyClass` třídy nejde vytvořit, protože funkce `MyClass::func2` není implementována. Chcete-li příklad zkompilovat, zrušte komentář u `MyClass::func2`.

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

##  <a name="BKMK_Type_visibility"></a> Viditelnost typů

Můžete řídit viditelnost běžné language runtime (CLR) typy tak, že pokud sestavení se odkazuje, typy v sestavení mohou být viditelná nebo není viditelný mimo sestavení.

`public` Označuje, že typ je viditelný do libovolného zdrojového souboru, který obsahuje `#using` směrnice pro sestavení, který obsahuje typ.  `private` Označuje, že typ není viditelný pro zdrojové soubory, které obsahují `#using` směrnice pro sestavení, který obsahuje typ. Privátní typy jsou však viditelné v rámci stejného sestavení. Výchozí viditelnost pro třídu je `private`.

Ve výchozím nastavení před Visual C++ 2005 musely nativní typy přístupnost public mimo sestavení. Povolit [upozornění kompilátoru (úroveň 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) můžete zobrazit, kde jsou správně použity privátní nativní typy. Použití [make_public](../preprocessor/make-public.md) – Direktiva pragma přidělit nativní typ v souboru zdrojového kódu, který nemůže změnit přístupnost public.

Další informace najdete v tématu [# direktiva using](../preprocessor/hash-using-directive-cpp.md).

Následující příklad ukazuje, jak deklarovat typy a určete jejich přístupnost a pak přístup k těmto typům v sestavení. Samozřejmě pokud sestavení, který má privátní typy se odkazuje pomocí `#using`pouze veřejné typy v sestavení jsou viditelné.

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

**Output**

```Output
in Public_Class
in Private_Class
in Private_Class_2
```

Teď Pojďme přepsat předchozí ukázce tak, aby je vytvořený jako knihovnu DLL.

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

Další příklad ukazuje, jak pro přístup k typům mimo sestavení. V této ukázce klient využívá komponentu, která je vytvořená v předchozím příkladu.

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

**Output**

```Output
in Public_Class
```

##  <a name="BKMK_Member_visibility"></a> Viditelnost členů

Můžete provádět přístup člena veřejné třídy z v rámci stejného sestavení liší od přístupu k němu z mimo sestavení pomocí dvojice specifikátory přístupu `public`, `protected`, a `private`

Tato tabulka shrnuje vliv různých specifikátory přístupu:

|Specifikátor|Efekt|
|---------------|------------|
|public|Člen je přístupný uvnitř i mimo sestavení.  Zobrazit [veřejné](../cpp/public-cpp.md) Další informace.|
|private|Člen není přístupný, ani mimo sestavení.  Zobrazit [privátní](../cpp/private-cpp.md) Další informace.|
|protected|Člen je přístupný uvnitř i mimo sestavení, ale pouze pro odvozené typy.  Zobrazit [chráněné](../cpp/protected-cpp.md) Další informace.|
|internal|Člen je veřejné uvnitř sestavení, ale privátní mimo sestavení.  `internal` je kontextové klíčové slovo.  Další informace najdete v tématu [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md).|
|veřejné chráněný - nebo - chráněné veřejné|Člen je veřejné uvnitř sestavení, ale chráněný mimo sestavení.|
|privátní chráněný - nebo - chráněné privátní|Člen je chráněný v sestavení, ale privátní mimo sestavení.|

Následující příklad ukazuje veřejný typ, který má členy, které jsou deklarovány pomocí jiné přístupnosti a potom zobrazí přístupu k těmto členům z uvnitř sestavení.

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

Nyní Vytvořme předchozí ukázce jako knihovnu DLL.

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

Následující příklad využívá komponenta, která se vytvoří v předchozí ukázce a tím ukazuje, jak pro přístup ke členům z mimo sestavení.

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

##  <a name="BKMK_Public_and_private_native_classes"></a> Veřejné a soukromé nativních tříd

Nativní typ může odkazovat ze spravovaného typu.  Funkce v spravovaného typu může trvat parametr, jehož typ je nativní struktury.  Pokud jsou v sestavení veřejné spravovaného typu a funkce, pak nativní typ musí také být veřejné.

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

Dále vytvořte souboru se zdrojovým kódem, která využívá nativní typ:

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

Nyní kompilace klienta:

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

##  <a name="BKMK_Static_constructors"></a> Statické konstruktory

Typ CLR – například třídy nebo struktury, může mít statický konstruktor, který slouží k inicializaci statické datové členy.  Statický konstruktor se nazývá nejvýše jednou a je volána před všechny statický člen typu přistupuje poprvé.

Konstruktor instance je spouštěn vždy po statický konstruktor.

Kompilátor nemůže provést vložení volání konstruktoru Pokud třída má statický konstruktor.  Kompilátor nemůže provést vložení volání žádnou členskou funkci třídy je typ hodnoty, má statický konstruktor a nemá konstruktor instance.  Modul CLR může vložené volání, ale kompilátor nemůže provést.

Definujte statický konstruktor jako funkci soukromého členu, protože je určená k volání pouze platformou CLR.

Další informace o statické konstruktory, naleznete v tématu [jak: Definování statického konstruktoru (C + +/ CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .

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

**Output**

```Output
in static constructor
10
11
```

##  <a name="BKMK_Semantics_of_the_this_pointer"></a> Sémantika tento ukazatel

Při použití jazyka Visual C++ k definování typů, `this` ukazatel v typu odkazu je typu "popisovač". `this` Ukazatele typu hodnota je typu "vnitřní ukazatel".

Tyto různé sémantiky `this` ukazatelů může způsobit neočekávané chování, když je zavolána výchozímu indexeru. Další příklad ukazuje správný způsob pro přístup k výchozímu indexeru v typu ref a typem hodnoty.

Další informace naleznete v tématu

- [Operátor popisovače objektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)

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

**Output**

```Output
10.89
10.89
```

##  <a name="BKMK_Hide_by_signature_functions"></a> Skrytí podle podpisu funkce

Ve standardním jazyce C++ funkce v základní třídě je skrytá ve funkci, která má stejný název v odvozené třídě, i v případě, že odvozené třídy funkce nemá stejný počet a druh parametry. To se označuje jako *skrýt podle názvu* sémantiku. V typu odkazu funkce v základní třídě můžete pouze být skryty pomocí funkce v odvozené třídě. Pokud název a seznamu parametrů jsou stejné. To se označuje jako *skrytí podle podpisu* sémantiku.

Třída je považován za třídu skrytí podle podpisu, pokud jsou všechny jeho funkce označené v metadatech jako `hidebysig`. Ve výchozím nastavení jsou všechny třídy, které jsou vytvořené v rámci **/CLR** mají `hidebysig` funkce. Pokud má třída `hidebysig` funkce, kompilátor neskryje funkce podle názvu v žádné přímé základní třídy, ale pokud kompilátor narazí na třídu skrýt název v řetěz dědičnosti, bude toto chování skrýt podle názvu.

V části skrytí podle podpisu sémantiku při volání funkce na objekt, kompilátor identifikuje nejvíce odvozenou třídu, která obsahuje funkce, která může splňovat volání funkce. Pokud existuje pouze jedna funkce ve třídě, která může splňovat volání, kompilátor volá tuto funkci. Pokud existuje více než jednu funkci ve třídě, která může splňovat volání, kompilátor používá přetížení pravidla řešení k určení funkce, které má být volána. Další informace o pravidlech přetížení, naleznete v tématu [přetížení funkce](../cpp/function-overloading.md).

Pro volání dané funkce funkce v základní třídě pravděpodobně podpis, který umožňuje o trochu lepší shody než funkce v odvozené třídě. Funkce byla explicitně volána na objektu odvozené třídy, je volána funkce v odvozené třídě.

Protože vrácená hodnota není považována za součást podpisu funkce, funkce základní třídy je skrytá Pokud má stejný název a má stejný počet a typ argumentů jako funkce odvozené třídy i v případě, že se liší v typu vrácené hodnoty.

Následující příklad ukazuje, že funkce v základní třídě není skryté funkce v odvozené třídě.

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

**Output**

```Output
Base::Test
```

Další příklad ukazuje, že kompilátor Visual C++ volá funkci v nejvíce odvozené třídy – i v případě, že převod je vyžadovaný pro shodu nejméně jeden z parametrů – a není volání funkce v základní třídě, která představuje lepší shodu pro volání funkce.

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

**Output**

```Output
Derived::Test2
```

Následující příklad ukazuje, že je možné skrýt funkci i v případě, že nemá stejný podpis jako odvozené třídy základní třídy.

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

**Output**

```Output
Derived::Test4
97
```

##  <a name="BKMK_Copy_constructors"></a> Kopírovací konstruktory

Standard jazyka C++ říká, že kopírovací konstruktor se volá, když je přesunout objekt, tak, že objekt je vytvořeno a zničeno na stejné adrese.

Ale když **/CLR** slouží ke kompilaci a funkci, která je kompilováno do jazyka MSIL volání nativní funkce tam, kde nativních tříd – nebo má více než jeden – je předán podle hodnoty a kdy má nativních tříd kopírovací konstruktor nebo destruktor, bez kopírování Konstruktor je volán a objekt je zničen na jinou adresu než ve kterém byla vytvořena. To může způsobit potíže, pokud třída má ukazatel na sebe sama, nebo pokud kód je objekty sledování podle adresy.

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

Následující příklad ukazuje, když se nevygeneroval kopírovací konstruktor.

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

##  <a name="BKMK_Destructors_and_finalizers"></a> Destruktory a finalizační metody

Destruktory v typu odkazu provádět deterministickou vyčištění prostředků. Finalizační metody vyčistit nespravované prostředky a může být volána nedeterministicky, destruktor nebo nedeterministicky systémem uvolňování. Informace o destruktorech ve standardním jazyce C++, naleznete v tématu [destruktory](../cpp/destructors-cpp.md).

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Chování destruktorů ve spravované třídě Visual C++ se liší od spravovaných rozšíření jazyka C++. Další informace o této změně najdete v tématu [změny v sémantice destruktorů](../dotnet/changes-in-destructor-semantics.md).

CLR systému uvolňování paměti odstraní nepoužitých spravovaných objektů a jejich paměť uvolní, když už nejsou povinné. Typ však mohou používat prostředky, které systému uvolňování paměti není známo, jak k uvolnění. Tyto prostředky jsou označovány jako nespravované prostředky (nativní soubor zpracovává, třeba). Doporučujeme, abyste uvolnění všech nespravovaných prostředků v finalizační metodu. Vzhledem k tomu, že spravované prostředky vydávají nedeterministicky systémem uvolňování, není bezpečné pro odkazování na spravované prostředky v finalizační metoda vzhledem k tomu je možné, že systému uvolňování paměti již vyčistila tento spravovaný prostředek.

Finalizační metoda Visual C++ není stejný jako <xref:System.Object.Finalize%2A> metody. (CLR dokumentace používá finalizační metody a <xref:System.Object.Finalize%2A> metoda jako synonyma). <xref:System.Object.Finalize%2A> Metoda je volána metodou systému uvolňování paměti, které vyvolá každý finalizační metody v řetězu dědičnosti třídy. Na rozdíl od destruktory jazyka Visual C++ finalizační metodu odvozené třídy volání nezpůsobí kompilátor volat finalizační metodu všech základních tříd.

Protože kompilátor Visual C++ podporuje deterministické uvolnění prostředků, nedoporučujeme provádět <xref:System.IDisposable.Dispose%2A> nebo <xref:System.Object.Finalize%2A> metody. Pokud jste obeznámeni s těmito metodami, tady je ale jak Visual C++ finalizační metody a destruktor, která volá finalizační metodu mapují na <xref:System.IDisposable.Dispose%2A> vzoru:

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

Spravovaný typ může použít také spravované prostředky, které chcete uvolnit deterministicky a nesmí zůstat na systému uvolňování paměti k uvolnění nedeterministicky v určitém okamžiku po objekt se už nevyžaduje. Deterministické uvolnění prostředků může výrazně zlepšit výkon.

Kompilátor Visual C++ umožňuje definice destruktor nedeterministicky vyčistit objekty. Můžete uvolnit všechny prostředky, které chcete uvolnit nedeterministicky destruktor.  Pokud se nachází finalizační metodu, jeho volání z destruktoru, aby se zabránilo duplicitě kódu.

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

Pokud kód, který využívá typ nevolá destruktor, systému uvolňování paměti uvolní nakonec všechny spravované prostředky.

Přítomnost destruktor neznamená přítomnost finalizační metodu. Přítomnost finalizační metody však znamená, že musíte definovat destruktor a volat finalizační metodu z této – destruktor. To umožňuje deterministické uvolnění nespravovaných prostředků.

Volání destruktoru potlačí – s použitím <xref:System.GC.SuppressFinalize%2A>– finalizaci objektu. Pokud je destruktor není volána, finalizační metodu pro váš typ bude nakonec volat systému uvolňování paměti.

Nedeterministicky uvolnění prostředků objektu voláním destruktoru může zlepšit výkon ve srovnání s umožníte tím CLR nedeterministicky finalizaci objektu.

Kód, který má napsaný v jazyce Visual C++ a zkompilován s použitím **/CLR** spustí destruktor typu, pokud:

- Objekt, který je vytvořen pomocí – sémantika zásobníku dostane mimo rozsah. Další informace najdete v tématu [C++ – sémantika zásobníku pro odkazové typy](../dotnet/cpp-stack-semantics-for-reference-types.md).

- Výjimka je vyvolána během konstrukce objektu.

- Objekt je člen v objektu, jehož destruktor je spuštěná.

- Volání [odstranit](../cpp/delete-operator-cpp.md) operátor na popisovač ([operátor popisovače objektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)).

- Explicitně zavolat destruktor.

Pokud váš typ spotřebovává klienta, která je napsána v jiném jazyce, je zavolán destruktor následujícím způsobem:

- Volání <xref:System.IDisposable.Dispose%2A>.

- Volání `Dispose(void)` na typu.

- Pokud typ dostane mimo rozsah v jazyce C# `using` příkazu.

Pokud vytvoříte objekt typu odkazu na spravované haldě (bez použití – sémantika zásobníku pro odkazové typy), použijte [try-finally](../cpp/try-finally-statement.md) syntaxe Ujistěte se, že výjimka nezabrání spuštění destruktoru.

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

Pokud váš typ má destruktor, kompilátor vygeneruje `Dispose` metody, která implementuje <xref:System.IDisposable>. Pokud typ, který je napsán v jazyce Visual C++ a má destruktor, která se využívá v jiném jazyce, volání `IDisposable::Dispose` u tohoto typu způsobí, že destruktor typu volat. Když typ je zpracován z klienta Visual C++, nelze volat přímo `Dispose`; místo toho zavolejte destruktor pomocí `delete` operátor.

Pokud váš typ má finalizační metodu, kompilátor vygeneruje `Finalize(void)` metodu, která přepíše <xref:System.Object.Finalize%2A>.

Pokud typ má finalizační metodu nebo destruktor, kompilátor vygeneruje `Dispose(bool)` metoda podle vzoru návrhu. (Informace najdete v tématu [vzor Dispose](/dotnet/standard/design-guidelines/dispose-pattern)). Nejde explicitně vytvářet nebo volání `Dispose(bool)` v jazyce Visual C++.

Pokud typ má základní třída, která odpovídá vzoru návrhu, destruktory pro všechny základní třídy jsou volány při je volán destruktor odvozené třídy. (Pokud váš typ je napsán v jazyce Visual C++, kompilátor pak zajistí, že tento model implementovat vaše typy.) Jinými slovy, destruktor třídy odkazu zřetězený jeho základních tříd a členů podle standardu jazyka C++ – první destruktor třídy je spustit a destruktory členů opakem pořadí, ve kterém byly vytvořeny, a nakonec destruktory pro její základní třídy opakem pořadí, ve kterém byly vytvořeny.

Destruktory a finalizační metody nejsou povolené uvnitř rozhraní nebo typy hodnot.

Finalizační metody pouze nelze definovat ani deklarovaného v typu odkazu. Jako konstruktor a destruktor finalizační metoda nemá žádný návratový typ.

Po spuštění finalizační metodu objektu finalizační metody v žádné základní třídy se také označují jako, od nejméně odvozeného typu. Finalizační metody pro datové členy nejsou zřetězené automaticky podle finalizační metodu třídy.

Pokud finalizační metody odstraní nativní ukazatel v spravovaného typu, musíte zajistit, že odkazy na nebo prostřednictvím nativní ukazatel se neshromažďují předčasně; Zavolejte destruktor na spravovaný typ namísto použití <xref:System.GC.KeepAlive%2A>.

V době kompilace můžete zjistit, zda má typ finalizační metodu nebo destruktor. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

Další příklad ukazuje dva typy, ten, který má nespravované prostředky a jeden, který se má spravovat prostředky, které se vydávají nedeterministicky.

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

## <a name="see-also"></a>Viz také:

[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)
