---
title: Uživatelem definované převody (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
ms.openlocfilehash: bb7a30382bc586f4d324d47ef6e6757fac83f5ae
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988386"
---
# <a name="user-defined-conversions-ccli"></a>Uživatelem definované převody (C++/CLI)

Tato část popisuje uživatelsky definované převody (UDC), pokud jeden z typů v převodu je odkazem nebo instancí typu hodnoty nebo odkazu.

## <a name="implicit-and-explicit-conversions"></a>Implicitní a explicitní převody

Uživatelsky definovaný převod může být buď implicitní, nebo explicitní.  UDC by měl být implicitní, pokud převod nevede ke ztrátě informací. V opačném případě by měl být definován explicitní UDC.

Konstruktor nativní třídy lze použít k převedení typu odkazu nebo hodnoty na nativní třídu.

Další informace o převodech naleznete v tématu [zabalení](../extensions/boxing-cpp-component-extensions.md) a [standardní převody](../cpp/standard-conversions.md).

```cpp
// mcpp_User_Defined_Conversions.cpp
// compile with: /clr
#include "stdio.h"
ref class R;
class N;

value class V {
   static operator V(R^) {
      return V();
   }
};

ref class R {
public:
   static operator N(R^);
   static operator V(R^) {
      System::Console::WriteLine("in R::operator N");
      return V();
   }
};

class N {
public:
   N(R^) {
      printf("in N::N\n");
   }
};

R::operator N(R^) {
   System::Console::WriteLine("in R::operator N");
   return N(nullptr);
}

int main() {
   // Direct initialization:
   R ^r2;
   N n2(r2);   // direct initialization, calls constructor
   static_cast<N>(r2);   // also direct initialization

   R ^r3;
   // ambiguous V::operator V(R^) and R::operator V(R^)
   // static_cast<V>(r3);
}
```

**Output**

```Output
in N::N
in N::N
```

## <a name="convert-from-operators"></a>Operátory Convert-From

Operátory Convert-From vytvoří objekt třídy, ve které je operátor definován z objektu některé jiné třídy.

Standard C++ nepodporuje operátory Convert-from; standard C++ používá pro tento účel konstruktory. Při použití typů CLR ale Visual C++ poskytuje syntaktickou podporu pro volání operátorů Convert-from.

Chcete-li spolupracovat s jinými jazyky kompatibilními se specifikací CLS, můžete chtít zabalit každý uživatelem definovaný unární konstruktor pro danou třídu s odpovídajícím operátorem Convert-from.

Operátory Convert-From:

- Musí být definován jako statické funkce.

- Může být buď implicitní (pro převody, které neztratí přesnost, jako je například short-to-int) nebo Explicit, pokud může dojít ke ztrátě přesnosti.

- Musí vrátit objekt obsahující třídu.

- Musí mít jako jediný typ parametru typ "od".

Následující příklad ukazuje implicitní a explicitní operátor "Convert-z", uživatelsky definovaný převod (UDC).

```cpp
// clr_udc_convert_from.cpp
// compile with: /clr
value struct MyDouble {
   double d;

   MyDouble(int i) {
      d = static_cast<double>(i);
      System::Console::WriteLine("in constructor");
   }

   // Wrap the constructor with a convert-from operator.
   // implicit UDC because conversion cannot lose precision
   static operator MyDouble (int i) {
      System::Console::WriteLine("in operator");
      // call the constructor
      MyDouble d(i);
      return d;
   }

   // an explicit user-defined conversion operator
   static explicit operator signed short int (MyDouble) {
      return 1;
   }
};

int main() {
   int i = 10;
   MyDouble md = i;
   System::Console::WriteLine(md.d);

   // using explicit user-defined conversion operator requires a cast
   unsigned short int j = static_cast<unsigned short int>(md);
   System::Console::WriteLine(j);
}
```

**Output**

```Output
in operator
in constructor
10
1
```

## <a name="convert-to-operators"></a>Operátory převodu na

Operátory Convert-to převádějí objekt třídy, ve které je operátor definován pro jiný objekt. Následující příklad ukazuje implicitní operátor převodu, který je definován uživatelem:

```cpp
// clr_udc_convert_to.cpp
// compile with: /clr
using namespace System;
value struct MyInt {
   Int32 i;

   // convert MyInt to String^
   static operator String^ ( MyInt val ) {
      return val.i.ToString();
   }

   MyInt(int _i) : i(_i) {}
};

int main() {
   MyInt mi(10);
   String ^s = mi;
   Console::WriteLine(s);
}
```

**Output**

```Output
10
```

Explicitní operátor převodu na převod, který je definován uživatelem, je vhodný pro převody, které mohou nějakým způsobem přijít o data. Chcete-li vyvolat explicitní operátor Convert-to, je nutné použít přetypování.

```cpp
// clr_udc_convert_to_2.cpp
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
   d.d = 10.3;
   System::Console::WriteLine(d.d);
   int i = 0;
   i = static_cast<int>(d);
   System::Console::WriteLine(i);
}
```

**Output**

```Output
10.3
10
```

## <a name="to-convert-generic-classes"></a>Převod obecných tříd

Můžete převést obecnou třídu na T.

```cpp
// clr_udc_generics.cpp
// compile with: /clr
generic<class T>
public value struct V {
   T mem;
   static operator T(V v) {
      return v.mem;
   }

   void f(T t) {
      mem = t;
   }
};

int main() {
   V<int> v;
   v.f(42);
   int i = v;
   i += v;
   System::Console::WriteLine(i == (42 * 2) );
}
```

**Output**

```Output
True
```

Převedený konstruktor přebírá typ a používá ho k vytvoření objektu.  Převedený konstruktor je volán pouze přímou inicializací; přetypování nebudou volat převod konstruktorů. Ve výchozím nastavení jsou převádění konstruktorů explicitní pro typy CLR.

```cpp
// clr_udc_converting_constructors.cpp
// compile with: /clr
public ref struct R {
   int m;
   char c;

   R(int i) : m(i) { }
   R(char j) : c(j) { }
};

public value struct V {
   R^ ptr;
   int m;

   V(R^ r) : ptr(r) { }
   V(int i) : m(i) { }
};

int main() {
   R^ r = gcnew R(5);

   System::Console::WriteLine( V(5).m);
   System::Console::WriteLine( V(r).ptr);
}
```

**Output**

```Output
5
R
```

V této ukázce kódu má implicitní statická funkce pro převod stejnou věc jako explicitní konstruktor převodu.

```
public value struct V {
   int m;
   V(int i) : m(i) {}
   static operator V(int i) {
      V v(i*100);
      return v;
   }
};

public ref struct R {
   int m;
   R(int i) : m(i) {}
   static operator R^(int i) {
      return gcnew R(i*100);
   }
};

int main() {
   V v(13);   // explicit
   R^ r = gcnew R(12);   // explicit

   System::Console::WriteLine(v.m);
   System::Console::WriteLine(r->m);

   // explicit ctor can't be called here: not ambiguous
   v = 5;
   r = 20;

   System::Console::WriteLine(v.m);
   System::Console::WriteLine(r->m);
}
```

**Output**

```Output
13
12
500
2000
```

## <a name="see-also"></a>Viz také:

[Třídy a struktury](../extensions/classes-and-structs-cpp-component-extensions.md)
