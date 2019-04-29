---
title: 'Postupy: Definice a používání delegátů (C++vyhodnocovací)'
ms.date: 11/04/2016
helpviewer_keywords:
- delegates
ms.assetid: 1cdf3420-89c1-47c0-b796-aa984020e0f8
ms.openlocfilehash: bcbf5bf978da5b6c13dd131e7a19975381bd97a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387367"
---
# <a name="how-to-define-and-use-delegates-ccli"></a>Postupy: Definice a používání delegátů (C++vyhodnocovací)

Tento článek ukazuje, jak definice a používání delegátů v C++vyhodnocovací.

Přestože rozhraní .NET Framework poskytuje delegáty, někdy budete muset definovat nové delegáty.

Následující příklad kódu definuje delegáta s názvem `MyCallback`. Kód pro zpracování událostí – funkce, která je volána, když se aktivuje tento nový delegát – musí mít typ vrácené hodnoty `void` a provést <xref:System.String> odkaz.

Hlavní funkce používá statickou metodu, která je definována `SomeClass` pro vytvoření instance `MyCallback` delegovat. Delegát se pak stane alternativní způsob volání této funkce, jak je ukázáno odesláním řetězec "jeden" objekt delegáta. Dál se další instance `MyCallback` jsou propojeny a potom provedených volání objektu delegáta.

```cpp
// use_delegate.cpp
// compile with: /clr
using namespace System;

ref class SomeClass
{
public:
   static void Func(String^ str)
   {
      Console::WriteLine("static SomeClass::Func - {0}", str);
   }
};

ref class OtherClass
{
public:
   OtherClass( Int32 n )
   {
      num = n;
   }

   void Method(String^ str)
   {
      Console::WriteLine("OtherClass::Method - {0}, num = {1}",
         str, num);
   }

   Int32 num;
};

delegate void MyCallback(String^ str);

int main( )
{
   MyCallback^ callback = gcnew MyCallback(SomeClass::Func);
   callback("single");

   callback += gcnew MyCallback(SomeClass::Func);

   OtherClass^ f = gcnew OtherClass(99);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   f = gcnew OtherClass(100);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   callback("chained");

   return 0;
}
```

```Output
static SomeClass::Func - single
static SomeClass::Func - chained
static SomeClass::Func - chained
OtherClass::Method - chained, num = 99
OtherClass::Method - chained, num = 100
```

Následující vzorový kód ukazuje, jak přidružit člena hodnotové třídy delegáta.

```cpp
// mcppv2_del_mem_value_class.cpp
// compile with: /clr
using namespace System;
public delegate void MyDel();

value class A {
public:
   void func1() {
      Console::WriteLine("test");
   }
};

int main() {
   A a;
   A^ ah = a;
   MyDel^ f = gcnew MyDel(a, &A::func1);   // implicit box of a
   f();
   MyDel^ f2 = gcnew MyDel(ah, &A::func1);
   f2();
}
```

```Output
test
test
```

## <a name="how-to-compose-delegates"></a>Postup vytváření delegátů

Můžete použít "`-`" operátor odebrání součástí delegáta složené delegáta.

```cpp
// mcppv2_compose_delegates.cpp
// compile with: /clr
using namespace System;

delegate void MyDelegate(String ^ s);

ref class MyClass {
public:
   static void Hello(String ^ s) {
      Console::WriteLine("Hello, {0}!", s);
   }

   static void Goodbye(String ^ s) {
      Console::WriteLine("  Goodbye, {0}!", s);
   }
};

int main() {

   MyDelegate ^ a = gcnew MyDelegate(MyClass::Hello);
   MyDelegate ^ b = gcnew MyDelegate(MyClass::Goodbye);
   MyDelegate ^ c = a + b;
   MyDelegate ^ d = c - a;

   Console::WriteLine("Invoking delegate a:");
   a("A");
   Console::WriteLine("Invoking delegate b:");
   b("B");
   Console::WriteLine("Invoking delegate c:");
   c("C");
   Console::WriteLine("Invoking delegate d:");
   d("D");
}
```

**Output**

```Output
Invoking delegate a:
Hello, A!
Invoking delegate b:
  Goodbye, B!
Invoking delegate c:
Hello, C!
  Goodbye, C!
Invoking delegate d:
  Goodbye, D!
```

## <a name="pass-a-delegate-to-a-native-function-that-expects-a-function-pointer"></a>Předání delegáta ^ nativní funkcí, která očekává ukazatel na funkci

Ze spravované součásti můžete volat nativní funkce pomocí funkce parametry ukazatele kde nativní funkce potom může zavolat členskou funkci delegáta spravované součásti.

Tato ukázka vytvoří soubor .dll, který exportuje nativní funkce:

```cpp
// delegate_to_native_function.cpp
// compile with: /LD
#include < windows.h >
extern "C" {
   __declspec(dllexport)
   void nativeFunction(void (CALLBACK *mgdFunc)(const char* str)) {
      mgdFunc("Call to Managed Function");
   }
}
```

Bude další vzorek využívá soubor .dll a předává popisovač delegáta nativní funkce, která očekává ukazatel na funkci.

```cpp
// delegate_to_native_function_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

delegate void Del(String ^s);
public ref class A {
public:
   void delMember(String ^s) {
      Console::WriteLine(s);
   }
};

[DllImportAttribute("delegate_to_native_function", CharSet=CharSet::Ansi)]
extern "C" void nativeFunction(Del ^d);

int main() {
   A ^a = gcnew A;
   Del ^d = gcnew Del(a, &A::delMember);
   nativeFunction(d);   // Call to native function
}
```

**Output**

```Output
Call to Managed Function
```

## <a name="to-associate-delegates-with-unmanaged-functions"></a>Přidružení delegátů k nespravovaným funkcím

Pokud chcete přidružit delegáta nativní funkce, musí obalí nativní funkce spravovaného typu a Deklarujte funkci, která má být volána prostřednictvím `PInvoke`.

```cpp
// mcppv2_del_to_umnangd_func.cpp
// compile with: /clr
#pragma unmanaged
extern "C" void printf(const char*, ...);
class A {
public:
   static void func(char* s) {
      printf(s);
   }
};

#pragma managed
public delegate void func(char*);

ref class B {
   A* ap;

public:
   B(A* ap):ap(ap) {}
   void func(char* s) {
      ap->func(s);
   }
};

int main() {
   A* a = new A;
   B^ b = gcnew B(a);
   func^ f = gcnew func(b, &B::func);
   f("hello");
   delete a;
}
```

**Output**

```Output
hello
```

## <a name="to-use-unbound-delegates"></a>Chcete-li použít nevázaní delegáti

Můžete předat instanci typu, jehož funkce chcete volat při volání delegáta delegáta bez vazby.

Nevázaní Delegáti jsou obzvláště užitečné, pokud chcete k iteraci v rámci objektů v kolekci – s použitím [u každé v](../dotnet/for-each-in.md) klíčová slova a zavolat členskou funkci na jednotlivých instancích.

Tady je postup, chcete-li deklarovat, vytvořit instanci a volání vázané a nevázaných delegáti:

|Akce|Vázaný delegátů|Nevázaní delegáti|
|------------|---------------------|-----------------------|
|Deklarace|Signatura delegáta musí odpovídat signatuře funkce, kterou chcete volat prostřednictvím delegáta.|První parametr delegáta je typu `this` pro objekt, který chcete volat.<br /><br /> Po první parametr delegáta musí odpovídat signatuře funkce, kterou chcete volat prostřednictvím delegáta.|
|Vytvoření instance|Když vytvoříte instanci delegátu vázaný, můžete zadat instance funkce nebo globální nebo statické členské funkce.<br /><br /> Pokud chcete zadat instance funkce, první parametr je instance typu, jehož členská funkce, kterou chcete volat a druhý parametr je adresa funkce, kterou chcete volat.<br /><br /> Pokud chcete volat globální nebo statická členská funkce, stačí pouze předejte název globální funkce nebo název statickou členskou funkci.|Při vytváření instance delegáta bez vazby, stačí pouze předejte adresu funkce, kterou chcete volat.|
|Volání|Při volání vázané delegáta, stačí pouze předejte parametry, které jsou vyžadované delegáta.|Stejné jako vazbu delegáta, ale mějte na paměti, že první parametr musí být instancí objektu, který obsahuje funkce, do které chcete volat.|

Tento příklad ukazuje, jak deklarovat, vytváření instancí a nevázaní delegáti volání:

```cpp
// unbound_delegates.cpp
// compile with: /clr
ref struct A {
   A(){}
   A(int i) : m_i(i) {}
   void Print(int i) { System::Console::WriteLine(m_i + i);}

private:
   int m_i;
};

value struct V {
   void Print() { System::Console::WriteLine(m_i);}
   int m_i;
};

delegate void Delegate1(A^, int i);
delegate void Delegate2(A%, int i);

delegate void Delegate3(interior_ptr<V>);
delegate void Delegate4(V%);

delegate void Delegate5(int i);
delegate void Delegate6();

int main() {
   A^ a1 = gcnew A(1);
   A% a2 = *gcnew A(2);

   Delegate1 ^ Unbound_Delegate1 = gcnew Delegate1(&A::Print);
   // delegate takes a handle
   Unbound_Delegate1(a1, 1);
   Unbound_Delegate1(%a2, 1);

   Delegate2 ^ Unbound_Delegate2 = gcnew Delegate2(&A::Print);
   // delegate takes a tracking reference (must deference the handle)
   Unbound_Delegate2(*a1, 1);
   Unbound_Delegate2(a2, 1);

   // instantiate a bound delegate to an instance member function
   Delegate5 ^ Bound_Del = gcnew Delegate5(a1, &A::Print);
   Bound_Del(1);

   // instantiate value types
   V v1 = {7};
   V v2 = {8};

   Delegate3 ^ Unbound_Delegate3 = gcnew Delegate3(&V::Print);
   Unbound_Delegate3(&v1);
   Unbound_Delegate3(&v2);

   Delegate4 ^ Unbound_Delegate4 = gcnew Delegate4(&V::Print);
   Unbound_Delegate4(v1);
   Unbound_Delegate4(v2);

   Delegate6 ^ Bound_Delegate3 = gcnew Delegate6(v1, &V::Print);
   Bound_Delegate3();
}
```

**Output**

```Output
2
3
2
3
2
7
8
7
8
7
```

Další příklad ukazuje, jak používat nevázaní Delegáti a [u každé v](../dotnet/for-each-in.md) klíčová slova k iteraci v rámci objektů v kolekci a zavolat členskou funkci na jednotlivých instancích.

```cpp
// unbound_delegates_2.cpp
// compile with: /clr
using namespace System;

ref class RefClass {
   String^ _Str;

public:
   RefClass( String^ str ) : _Str( str ) {}
   void Print() { Console::Write( _Str ); }
};

delegate void PrintDelegate( RefClass^ );

int main() {
   PrintDelegate^ d = gcnew PrintDelegate( &RefClass::Print );

   array< RefClass^ >^ a = gcnew array<RefClass^>( 10 );

   for ( int i = 0; i < a->Length; ++i )
      a[i] = gcnew RefClass( i.ToString() );

   for each ( RefClass^ R in a )
      d( R );

   Console::WriteLine();
}
```

Tato ukázka vytvoří delegáta bez vazby na vlastnosti přístupového objektu funkce:

```cpp
// unbound_delegates_3.cpp
// compile with: /clr
ref struct B {
   property int P1 {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }

private:
   int m_i;
};

delegate void DelBSet(B^, int);
delegate int DelBGet(B^);

int main() {
   B^ b = gcnew B;

   DelBSet^ delBSet = gcnew DelBSet(&B::P1::set);
   delBSet(b, 11);

   DelBGet^ delBGet = gcnew DelBGet(&B::P1::get);
   System::Console::WriteLine(delBGet(b));
}
```

**Output**

```Output
11
```

Následující příklad ukazuje, jak vyvolat vícesměrového vysílání delegáta, přičemž jedna instance je vázán a nevázaného jednu instanci.

```cpp
// unbound_delegates_4.cpp
// compile with: /clr
ref class R {
public:
   R(int i) : m_i(i) {}

   void f(R ^ r) {
      System::Console::WriteLine("in f(R ^ r)");
   }

   void f() {
      System::Console::WriteLine("in f()");
   }

private:
   int m_i;
};

delegate void Del(R ^);

int main() {
   R ^r1 = gcnew R(11);
   R ^r2 = gcnew R(12);

   Del^ d = gcnew Del(r1, &R::f);
   d += gcnew Del(&R::f);
   d(r2);
};
```

**Output**

```Output
in f(R ^ r)
in f()
```

Další příklad ukazuje, jak vytvořit a volat obecného delegáta bez vazby.

```cpp
// unbound_delegates_5.cpp
// compile with: /clr
ref struct R {
   R(int i) : m_i(i) {}

   int f(R ^) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

value struct V {
   int f(V%) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

generic <typename T>
delegate int Del(T t);

generic <typename T>
delegate int DelV(T% t);

int main() {
   R^ hr = gcnew R(7);
   System::Console::WriteLine((gcnew Del<R^>(&R::f))(hr));

   V v;
   v.m_i = 9;
   System::Console::WriteLine((gcnew DelV<V >(&V::f))(v) );
}
```

**Output**

```Output
12
14
```

## <a name="see-also"></a>Viz také:

[delegate (rozšíření komponent C++)](../extensions/delegate-cpp-component-extensions.md)
