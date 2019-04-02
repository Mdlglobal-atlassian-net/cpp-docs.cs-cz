---
title: Compiler Error C2440
ms.date: 03/28/2017
f1_keywords:
- C2440
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
ms.openlocfilehash: c85a8284c91037e981f0d1ea82507b49be8121a3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780675"
---
# <a name="compiler-error-c2440"></a>Compiler Error C2440

'conversion': nelze převést z 'type1' na 'type2'

Kompilátor nelze převést z `type1` k `type2`.

## <a name="example"></a>Příklad

C2440 může nastat, pokud se pokusíte inicializovat nekonstantní `char*` (nebo `wchar_t*`) pomocí řetězcového literálu v kódu jazyka C++, když možnost přizpůsobení kompilátoru [/Zc: strictstrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) nastavena. V jazyce C je typ řetězcového literálu pole `char`, ale v jazyce C++ je pole `const char`. Tato ukázka generuje upozornění C2440:

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

C2440 může také zapříčinit, pokud při pokusu o převod ukazatele na člen na void *. Následující ukázka generuje upozornění C2440:

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

C2440 může také zapříčinit, pokud při pokusu o přetypování z typu, který je deklarován pouze vpřed, ale není definovaný. Tato ukázka generuje upozornění C2440:

```cpp
// c2440a.cpp
struct Base { }; // Defined

struct Derived; // Forward declaration, not defined

Base * func(Derived * d) {
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'
}
```

## <a name="example"></a>Příklad

Chyby C2440 v řádcích 15 a 16 Další ukázky jsou kvalifikované `Incompatible calling conventions for UDT return value` zprávy. A *UDT* je typ definovaný uživatelem, jako je například třída, struktura nebo sjednocení. Tyto druhy chyb nekompatibility jsou způsobeny, když je konvence volání UDT zadaný v návratovém typu dopředné deklarace je v konfliktu se skutečnou konvencí volání UDT a když je zahrnuta ukazatele na funkci.

V tomto příkladu nejdřív existují dopředné deklarace pro strukturu a funkci, která vrátí strukturu; kompilátor předpokládá, že struktura používá konvenci volání jazyka C++. Dále je definice struktury, která standardně používá konvence volání. Vzhledem k tomu, že kompilátor nezná konvence volání struktury, dokud nedokončí čtení celé struktury, konvence volání pro strukturu v návratovém typu `get_c2` se také považuje za C++.

Struktura je následována jinou deklarací funkce, která vrátí strukturu, ale v tomto okamžiku kompilátor ví, že je struktura, obsahovat konvence volání C++. Podobně ukazatel funkce, která vrátí strukturu, je definován po definici struktury tak, aby kompilátor ví, že struktura používá konvenci volání jazyka C++.

Chcete-li vyřešit chybu C2440, která nastává z důvodu nekompatibilních konvencí volání, deklarujte funkce vracející typ definovaný uživatelem po definici UDT.

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

C2440 může vzniknout také v případě, že přiřadíte nulový vnitřní ukazatel:

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

C2440 může vzniknout také kvůli nesprávnému použití uživatelem definovaného převodu. Například pokud operátor převodu byl definovaný jako `explicit`, kompilátor nelze použít v implicitní převod. Další informace o uživatelem definovaných převodů, naleznete v tématu [uživatelem definovaných převodů (C + +/ CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)). Tato ukázka generuje upozornění C2440:

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

C2440 může vzniknout také při pokusu o vytvoření instance pole Visual C++, jehož typ je <xref:System.Array>.  Další informace najdete v tématu [pole](../../extensions/arrays-cpp-component-extensions.md).  Následující ukázka generuje upozornění C2440:

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

C2440 může vzniknout také z důvodu změn ve funkci atributů.  Následující ukázka generuje upozornění C2440.

```cpp
// c2440f.cpp
// compile with: /LD
[ module(name="PropDemoLib", version=1.0) ];   // C2440
// try the following line instead
// [ module(name="PropDemoLib", version="1.0") ];
```

## <a name="example"></a>Příklad

Kompilátor Visual C++ již neumožňuje [operátor const_cast](../../cpp/const-cast-operator.md) pro přetypování směrem dolů, když zdrojový kód, který používá **/CLR** programování je zkompilován.

Chcete-li vyřešit tuto chybu C2440, použijte správný operátor osazení. Další informace najdete v tématu [operátory přetypování](../../cpp/casting-operators.md).

Tato ukázka generuje upozornění C2440:

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

C2440 může vzniknout z důvodu změn v shoda kompilátoru v sadě Visual Studio 2015 Update 3. Dříve, kompilátor nesprávně považován za určité odlišné výrazy stejného typu při identifikaci odpovídající šablonu `static_cast` operace. Nyní kompilátor rozlišuje typy správně a kód, který spoléhal na předchozí `static_cast` chování je poškozená. Chcete-li tento problém vyřešit, změňte argument šablony pro odpovídat typu parametru šablony, nebo použít `reinterpret_cast` nebo přetypování C-style.

Tato ukázka generuje upozornění C2440:

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

### <a name="copy-list-initialization"></a>Inicializace kopírování seznamu

Visual Studio 2017 a novější správně vyvolat chyby při kompilaci vztahující se k vytvoření objektu pomocí inicializační seznamy, které nebyly byla zachycena v sadě Visual Studio 2015 a může způsobit selhání nebo nedefinované chování za běhu. V C ++ 17 kopírování Inicializace seznamu kompilátor je potřeba vzít v úvahu explicitní konstruktor pro řešení přetížení, ale musí vyvolat chybu, pokud je ve skutečnosti zvolená tohoto přetížení.

Následující příklad se zkompiluje ve Visual Studiu 2015 ale není v sadě Visual Studio 2017.

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

Chcete-li opravit chybu, použijte přímé inicializace:

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

### <a name="cv-qualifiers-in-class-construction"></a>Kvalifikátory CV v konstrukci třídy

V sadě Visual Studio 2015 kompilátor někdy nesprávně ignoruje kvalifikátor cv-qualifier při generování objektu třídy prostřednictvím volání konstruktoru. To může potenciálně způsobit selhání nebo neočekávané chování za běhu. Následující příklad zkompiluje ve Visual Studiu 2015 ale vyvolá kompilátor chybu v sadě Visual Studio 2017 a novější:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Chcete-li opravit chybu, deklarujte operátor int() jako const.
