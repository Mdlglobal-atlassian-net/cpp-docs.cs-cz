---
title: "Uživatelem definované převody (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 329461338579dc0787c6e3d208abac89ec762004
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-conversions-ccli"></a>Uživatelem definované převody (C++/CLI)
Tato část popisuje uživatelem definované převody (UDC), pokud jeden z typů v převodu odkaz nebo instance hodnota typu nebo typ odkazu.  
  
## <a name="implicit-and-explicit-conversions"></a>Implicitní a explicitní převody  
 Uživatelem definovaný převod může být buď implicitním nebo explicitním.  UDC by měl být implicitní, pokud převod neměla za následek ztrátu informací. V opačném případě by měl být definován explicitní UDC.  
  
 Konstruktor nativních tříd lze použít k převodu typu hodnotou nebo odkazem na nativních tříd.  
  
 Další informace o převody najdete v tématu [zabalení](../windows/boxing-cpp-component-extensions.md) a [standardní převody](../cpp/standard-conversions.md).  
  
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
 Operátory Convert-from vytvořit objekt třídy, ve kterém je definovaný operátor z objektu jiné třídy.  
  
 Standardní C++ nepodporuje operátory convert-from; standardní C++ používá konstruktory pro tento účel. Ale pokud používáte typy CLR, Visual C++ podporují syntaxi volání operátory convert-from.  
  
 Vzájemnou spolupráci s jinými kompatibilní se specifikací CLS jazyky, můžete chtít zabalení každé uživatelské unární konstruktor pro danou třídu s odpovídající operátor convert-from.  
  
 Operátory Convert-from:  
  
-   Musí být definován jako statické funkce.  
  
-   Buď lze (pro převody, které není ztratit přesnost například krátké int) implicitním nebo explicitním, když může být ztrátu přesnosti.  
  
-   Vrátí objekt obsahující třídy.  
  
-   Musí být typu "od" jako jediný parametr.  
  
 Následující příklad ukazuje implicitní a explicitní "convert-from", operátor uživatelem definované převodu (UDC).  
  
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
 Operátory Convert-to převést objekt třídy, ve kterém je definovaný operátor některé další objekt. Následující příklad ukazuje implicitní, convert-to, uživatelem definovaný převod operátor:  
  
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
  
 Operátor převodu explicitního uživatelem definované convert-to je vhodné pro převody, které by dojít ke ztrátě dat nějakým způsobem. K vyvolání explicitní operátor convert, se musí použít přetypování.  
  
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
 Obecné třídy můžete převést T.  
  
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
  
 Převod konstruktor trvá typu a použije k vytvoření objektu.  Převod konstruktor je volán s přímé inicializace pouze; konstruktory převodu nebude vyvolání přetypování. Konstruktory převodu jsou ve výchozím nastavení explicitní pro typy CLR.  
  
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
  
 Implicitní převod statické funkce v této ukázce kódu, provede stejnou akci jako konstruktor explicitní převod.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)