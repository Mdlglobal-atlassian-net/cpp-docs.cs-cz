---
title: C2440 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2440
dev_langs:
- C++
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6b03dfc413e3a63e5084dc265d5b7010fbcebd4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235072"
---
# <a name="compiler-error-c2440"></a>C2440 chyby kompilátoru
'Převod': nelze převést na 'type2' 'type1'  
  
Kompilátor nelze přetypovat z `type1` k `type2`.  
  
## <a name="example"></a>Příklad  
C2440 může dojít, pokud se pokusíte k chybě při inicializaci jiný const `char*` (nebo `wchar_t*`) pomocí řetězcový literál v kódu C++, když shoda možnost kompilátoru [/Zc: strictstrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) nastavena. V jazyce C, typ řetězcový literál je pole `char`, ale v jazyce C++, je pole `const char`. Tato ukázka generuje C2440:  
  
```cpp  
// C2440s.cpp  
// Build: cl /Zc:strictStrings /W3 C2440s.cpp  
// When built, the compiler emits:  
// error C2440: 'initializing' : cannot convert from 'const char [5]'   
// to 'char *'  
//        Conversion from string literal loses const qualifier (see  
// /Zc:strictStrings)  
  
int main() {  
   char* s1 = "test"; // C2440  
   const char* s2 = "tests"; // OK  
}  
```  
  
## <a name="example"></a>Příklad  
 C2440 může také dojít, pokud se pokusíte převést ukazatele na člena void *. Další vzorek generuje C2440:  
  
```cpp  
// C2440.cpp  
class B {  
public:  
   void  f(){;}  
  
   typedef void (B::*pf)();  
  
   void f2(pf pf) {  
       (this->*pf)();  
       void* pp = (void*)pf;   // C2440  
   }  
  
   void f3() {  
      f2(f);  
   }  
};  
```  
  
## <a name="example"></a>Příklad  
 C2440 může být též situace, pokud se pokusíte převést z typu, který je deklarován pouze dopředu, ale není definován. Tato ukázka generuje C2440:  
  
```cpp  
// c2440a.cpp   
struct Base { }; // Defined  
  
struct Derived; // Forward declaration, not defined  
  
Base * func(Derived * d) {  
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'  
}  
  
```  
  
## <a name="example"></a>Příklad  
 C2440 chyby na řádcích 15 a 16 bude další vzorek jsou kvalifikovaný pomocí `Incompatible calling conventions for UDT return value` zprávy. A *UDT* je uživatelsky definovaný typ., například třída, struktura nebo union. Tyto druhy chyb nekompatibilita způsobuje Pokud konvence volání UDT zadaný v návratový typ předat dál deklarace je v konfliktu s skutečné konvence volání UDT a pokud je zahrnuta ukazatel na funkci.  
  
 V příkladu nejprve nejsou dopředně deklarace pro struktury a funkci, která vrátí struktura; kompilátor předpokládá, že struct používá C++ konvence volání. Dále je definici struktura, která ve výchozím nastavení používá C konvence volání. Protože kompilátor nebude vědět konvence volání dané struktury, dokud neskončí čtení celá struktura konvence volání pro struktura v návratový typ `get_c2` také předpokládá se, že C++.  
  
 Struct následuje jiný deklarace funkce, která vrací struct, ale v tomto okamžiku kompilátor ví, že je struktura konvence volání C++. Podobně po definování struktura je definována ukazatel na funkci, která vrátí struct, tak, aby kompilátor ví, že struct používá C++ konvence volání.  
  
 Chcete-li vyřešit C2440, ke kterému dochází z důvodu nekompatibilní konvence volání, deklarujte funkce, které vrací typ definovaný uživatelem po definování UDT.  
  
```cpp  
// C2440b.cpp  
struct MyStruct;  
  
MyStruct get_c1();  
  
struct MyStruct {  
   int i;  
   static MyStruct get_C2();  
};  
  
MyStruct get_C3();  
  
typedef MyStruct (*FC)();  
  
FC fc1 = &get_c1;   // C2440, line 15  
FC fc2 = &MyStruct::get_C2;   // C2440, line 16  
FC fc3 = &get_C3;  
  
class CMyClass {  
public:  
   explicit CMyClass( int iBar)  
      throw()   {  
   }  
  
   static CMyClass get_c2();  
};  
  
int main() {  
   CMyClass myclass = 2;   // C2440  
   // try one of the following  
   // CMyClass myclass{2};  
   // CMyClass myclass(2);  
  
   int *i;  
   float j;  
   j = (float)i;   // C2440, cannot cast from pointer to int to float  
}  
```  
  
## <a name="example"></a>Příklad  
 C2440 může také nastat, pokud přiřadíte nula na vnitřní ukazatel:  
  
```cpp  
// C2440c.cpp  
// compile with: /clr  
int main() {  
   array<int>^ arr = gcnew array<int>(100);  
   interior_ptr<int> ipi = &arr[0];  
   ipi = 0;   // C2440  
   ipi = nullptr;   // OK  
}  
```  
  
## <a name="example"></a>Příklad  
 C2440 může dojít také pro nesprávné použití převod definovaný uživatelem. Například když operátora převodu byla definována jako `explicit`, kompilátor nelze použít v implicitní převod. Další informace o uživatelem definovaných převodů najdete v tématu [uživatelem definovaných převodů (C + +/ CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)). Tato ukázka generuje C2440:  
  
```cpp  
// C2440d.cpp  
// compile with: /clr  
value struct MyDouble {  
   double d;  
   // convert MyDouble to Int32  
   static explicit operator System::Int32 ( MyDouble val ) {  
      return (int)val.d;  
   }  
};  
  
int main() {  
   MyDouble d;  
   int i;  
   i = d;   // C2440  
   // Uncomment the following line to resolve.  
   // i = static_cast<int>(d);  
}  
```  
  
## <a name="example"></a>Příklad  
 C2440 může také nastat, pokud se pokusíte vytvořit instanci třídy Visual C++ pole, jejichž typ je <xref:System.Array>.  Další informace najdete v tématu [pole](../../windows/arrays-cpp-component-extensions.md).  Další vzorek generuje C2440:  
  
```cpp  
// C2440e.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   array<int>^ intArray = Array::CreateInstance(__typeof(int), 1);   // C2440  
   // try the following line instead  
   // array<int>^ intArray = safe_cast<array<int> ^>(Array::CreateInstance(__typeof(int), 1));  
}  
```  
  
## <a name="example"></a>Příklad  
 C2440 může dojít také z důvodu změn ve funkci atributy.  Následující ukázka generuje C2440.  
  
```cpp  
// c2440f.cpp  
// compile with: /LD  
[ module(name="PropDemoLib", version=1.0) ];   // C2440  
// try the following line instead  
// [ module(name="PropDemoLib", version="1.0") ];  
```  
  
## <a name="example"></a>Příklad  
 Visual C++ compiler již neumožňuje [const_cast – operátor](../../cpp/const-cast-operator.md) přetypovat dolů, kdy zdrojový kód, který používá **/CLR** kompiluje programování.  
  
 Chcete-li vyřešit tento C2440, použijte operátor správné přetypování. Další informace najdete v tématu [operátory přetypování](../../cpp/casting-operators.md).  
  
 Tato ukázka generuje C2440:  
  
```cpp  
// c2440g.cpp  
// compile with: /clr  
ref class Base {};  
ref class Derived : public Base {};  
int main() {  
   Derived ^d = gcnew Derived;  
   Base ^b = d;  
   d = const_cast<Derived^>(b);   // C2440  
   d = dynamic_cast<Derived^>(b);   // OK  
}  
```  
  
## <a name="example"></a>Příklad  
C2440 může dojít v důsledku změny shoda kompilátoru v sadě Visual Studio 2015 Update 3. Dříve, kompilátor nesprávně určité odlišné výrazy při považována za stejný typ identifikace odpovídající šablonu `static_cast` operaci. Nyní správně odlišuje typy a kód, který spoléhali na předchozí `static_cast` chování je poškozená. Chcete-li tento problém vyřešit, změňte argument šablony shodovat s typem parametru šablony, nebo použijte `reinterpret_cast` nebo přetypování ve stylu C.
  
Tato ukázka generuje C2440:  
  
```cpp  
// c2440h.cpp

template<int *a>
struct S1 {};

int g;
struct S2 : S1<&g> {
};

int main()
{
    S2 s;
    static_cast<S1<&*&g>>(s); // C2440 in VS 2015 Update 3 
    // This compiles correctly:
    // static_cast<S1<&g>>(s);
}

This error can appear in ATL code that uses the SINK_ENTRY_INFO macro defined in <atlcom.h>.

```

## <a name="example"></a>Příklad  
### <a name="copy-list-initialization"></a>Kopie – seznam – inicializace

Visual Studio 2017 a novější správně vyvolat chyby kompilátoru vztahující se k vytvoření objektu pomocí inicializátoru seznamů, které nebyly provedeny v sadě Visual Studio 2015 a může způsobit selhání nebo modul runtime chování není definován. V C ++ 17 kopírování – seznam inicializace kompilátor je potřeba vzít v úvahu explicitní konstruktor pro rozlišení přetížení, ale musíte zvýšit chybu, pokud je ve skutečnosti vybrali této přetížení.

Následující příklad zkompiluje v sadě Visual Studio 2015, ale není v Visual Studio 2017.

```cpp  
// C2440j.cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot 
                         // convert from 'int' to 'const A &'
}
```  
  
Chcete-li chybu opravit, použijte přímé inicializace:  
  
```cpp  
// C2440k.cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    const A& a2{ 1 };
}  
```  

## <a name="example"></a>Příklad
### <a name="cv-qualifiers-in-class-construction"></a>Kvalifikátory odchylka nákladů ve vytváření – třída

V sadě Visual Studio 2015 kompilátor někdy nesprávně ignoruje kvalifikátor odchylka nákladů při generování objektu třídy prostřednictvím volání konstruktoru. To může potenciálně způsobit havárie nebo neočekávané modul runtime chování. Následující příklad zkompiluje v sadě Visual Studio 2015, ale vyvolá chybu kompilátoru Visual Studio 2017 a novější:

```cpp
struct S 
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Chcete-li k chybě, deklarujte operátor int() jako const.
