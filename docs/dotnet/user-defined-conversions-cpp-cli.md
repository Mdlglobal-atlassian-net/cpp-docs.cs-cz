---
title: Uživatelem definované převody (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
ms.openlocfilehash: 8f168582e56e77f1ec848928b7ffd36879ba341a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384527"
---
# <a name="user-defined-conversions-ccli"></a>Uživatelem definované převody (C++/CLI)

Tato část popisuje uživatelem definované převody (UDC), pokud jeden z typů v převodu je odkaz nebo instanci hodnotového typu nebo typ odkazu.

## <a name="implicit-and-explicit-conversions"></a>Implicitní a explicitní převody

Uživatelem definovaný převod může být implicitní nebo explicitní.  UDC by měl být implicitní, pokud převod nemá za následek ztrátu informací. V opačném případě musí být definován explicitní UDC.

Konstruktor nativních tříd lze použít pro převod na nativních tříd typu odkazu nebo hodnoty.

Další informace o převodech viz [zabalení](../extensions/boxing-cpp-component-extensions.md) a [standardní převody](../cpp/standard-conversions.md).

```
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

Operátory Convert-from vytvoření objektu třídy, ve kterém je operátor definován z objektu jiné třídy.

Standardní C++ nepodporuje operátory convert-from; standardní C++ používá konstruktory pro tento účel. Ale při použití typů CLR, Visual C++ podporují syntaxi volání operátory convert-from.

Pro spolupráci dobře s jinými jazyky kompatibilní se Specifikací CLS, můžete chtít zabalit každý unární uživatelem definovaný konstruktor pro danou třídu s odpovídající operátor convert ze.

Operátory Convert-from:

- Musí být definován jako statické funkce.

- Můžete buď být implicitní (pro převody, které nejsou ztratit přesnost například krátké int) nebo explicitní, může dojít ke ztrátě přesnosti.

- Vrátí objekt obsahující třídy.

- Musí být typu "z" jako jediný parametr.

Následující příklad ukazuje implicitní a explicitní "convert-from", uživatelem definovaného převodu (UDC) operátor.

```
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

## <a name="convert-to-operators"></a>Operátory Convert-to

Operátory Convert-to převést objekt třídy, ve kterém je operátor definován na některý objekt. Následující příklad ukazuje implicitní, convert pro, uživatelem definovaný převod operátor:

```
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

Operátor převodu explicitního uživatelem definované convert-to je vhodné pro převody, které případně může přijít o data nějakým způsobem. Abyste mohli vyvolat explicitní operátor convert, musí použít přetypování.

```
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

## <a name="to-convert-generic-classes"></a>Chcete-li převést obecné třídy

Obecné třídy lze převést na T.

```
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

Převod konstruktor přijímá typ a použije ho k vytvoření objektu.  S přímou inicializací pouze; se nazývá konstruktor převodu přetypování nebude volat konstruktory převodu. Ve výchozím nastavení jsou konstruktory převodu explicitní pro typy CLR.

```
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

V této ukázce kódu implicitní statická funkce pro převod udělá to stejné jako konstruktor explicitní převod.

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
