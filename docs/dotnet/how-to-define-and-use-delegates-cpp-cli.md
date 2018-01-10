---
title: "Postupy: definice a používání delegátů (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: delegates
ms.assetid: 1cdf3420-89c1-47c0-b796-aa984020e0f8
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7f400a03f1b9ae877ee7ec681cb038698a92598a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-define-and-use-delegates-ccli"></a>Postupy: Definice a používání delegátů (C++/CLI)
Tento článek ukazuje, jak definice a používání delegátů v jazyce C + +/ CLI.  
  
 I když rozhraní .NET Framework poskytuje řadu delegáti, někdy pravděpodobně muset definovat nové delegáti.  
  
 Následující příklad kódu definuje delegáta, který je pojmenován `MyCallback`. Kód pro zpracování události – funkce, která je volána, když je aktivována, tento nový delegát – musí mít návratový typ `void` a proveďte <xref:System.String> odkaz.  
  
 Hlavní funkce používá statickou metodu, která je definovaná pomocí `SomeClass` k vytváření instancí `MyCallback` delegovat. Delegát se pak stane alternativní metodu volání této funkce, jak je předvedeno odesláním řetězec "jedné" objekt delegáta. Další, další instance `MyCallback` jsou propojeny společně a pak spustit jedno volání k objektu delegáta.  
  
```  
  
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
  
 **Output**  
  
```Output  
static SomeClass::Func - single  
static SomeClass::Func - chained  
static SomeClass::Func - chained  
OtherClass::Method - chained, num = 99  
OtherClass::Method - chained, num = 100  
```  
  
 Další příklad ukazuje, jak přidružit členem – hodnotová třída delegáta.  
  
```  
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
  
 **Output**  
  
```Output  
test  
test  
```  
  
## <a name="how-to-compose-delegates"></a>Postup vytváření delegátů  
 Můžete použít "`-`" operátor delegáta součást odebrání složený delegáta.  
  
```  
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
  
## <a name="pass-a-delegate-to-a-native-function-that-expects-a-function-pointer"></a>Předání delegáta ^ nativní funkce, která očekává ukazatel na funkci  
 Z spravované součásti můžete volat nativní funkce pomocí funkce ukazatel parametry kde nativní funkce pak můžete volat členské funkce delegáta spravované součásti.  
  
 Tato ukázka vytvoří .dll, který exportuje nativní funkce:  
  
```  
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
  
 Další vzorek využívá knihovna .dll a předá popisovač delegáta nativní funkce, která očekává ukazatel na funkci.  
  
```  
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
 Chcete-li přidružit nativní funkce delegáta, musíte zalomení nativní funkce v spravovaného typu a deklarovat funkce, která má být volána prostřednictvím `PInvoke`.  
  
```  
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
 Nevázaný delegáta můžete předat instanci typu jejichž funkce, kterou chcete volat při volání delegáta.  
  
 Nevázaní Delegáti jsou zvláště užitečné, pokud chcete použít k iteraci v rámci objektů v kolekcích – pomocí [, v](../dotnet/for-each-in.md) klíčová slova – a volat členské funkce na každou instanci.  
  
 Zde je postup deklarování, vytváření instancí a vázán volání a delegáti nevázaných:  
  
|Akce|Vázaný delegáti|Nevázaní delegáti|  
|------------|---------------------|-----------------------|  
|Deklarace|Delegáta musí odpovídat podpis funkce, kterou chcete volat prostřednictvím delegáta.|První parametr delegáta je typ `this` pro objekt, který chcete použít.<br /><br /> Po první parametr se musí shodovat delegáta podpis funkce, kterou chcete volat prostřednictvím delegáta.|  
|Vytváření instancí|Pokud instanci můžete vytvořit vázané delegáta, můžete instanci funkce nebo globální nebo statické členské funkce.<br /><br /> Pokud chcete zadat funkce instance, první parametr je instance typu jejichž – členská funkce chcete volat a druhý parametr je adresa funkce, kterou chcete volat.<br /><br /> Pokud chcete volat globální nebo statické členské funkce, stačí předejte název globální funkce nebo název funkce statický člen.|Pokud instanci můžete vytvořit nevázaný delegáta, stačí předejte adresu funkce, kterou chcete volat.|  
|Volání|Když zavoláte vázané delegáta, stačí předejte parametry, které jsou vyžadované delegáta.|Stejné jako hranice delegovat, ale mějte na paměti, že první parametr musí být instance objektu, který obsahuje funkce, kterou chcete volat.|  
  
 Tento příklad ukazuje, jak deklarování, vytváření instancí a volání nevázaní delegáti:  
  
```  
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
  
 Další příklad ukazuje způsob použití nevázaní Delegáti a [, v](../dotnet/for-each-in.md) klíčová slova a iteraci v rámci objektů v kolekcích volání členské funkce na každou instanci.  
  
```  
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
  
 Tato ukázka vytvoří delegáta nevázaný na funkce vlastnosti přístupového objektu:  
  
```  
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
  
 Následující příklad ukazuje, jak má být vyvolán vícesměrového vysílání delegáta, kde jedna instance je vázán a jedna instance nevázaný.  
  
```  
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
  
 Další příklad ukazuje postup vytvoření a volání nevázaný obecný delegát.  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [delegate (rozšíření komponent C++)](../windows/delegate-cpp-component-extensions.md)