---
title: "Postupy: používání sledovacích odkazů v jazyce C + +/ CLI | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CLR types, passing by reference
ms.assetid: d91e471c-34ff-4786-9e0d-c6db0494b946
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f7e03106c9a4e49e727e278538ca984b740ad446
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-tracking-references-in-ccli"></a>Postupy: Používání sledovacích odkazů v jazyce C++/CLI
Tento článek ukazuje, jak používat sledovací odkaz (%) v jazyce C + +/ CLI předat common language runtime (CLR) typy odkazem.  
  
## <a name="to-pass-clr-types-by-reference"></a>Předávání typů CLR odkazem  
 Následující příklad ukazuje, jak použít sledovací odkaz k předání odkazem typy CLR.  
  
```cpp  
// tracking_reference_handles.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct City {  
private:  
   Int16 zip_;  
  
public:  
   City (int zip) : zip_(zip) {};  
   property Int16 zip {  
      Int16 get(void) {  
         return zip_;  
      }   // get  
   }   // property  
};  
  
void passByRef (City ^% myCity) {  
   // cast required so this pointer in City struct is "const City"  
   if (myCity->zip == 20100)  
      Console::WriteLine("zip == 20100");  
   else  
      Console::WriteLine("zip != 20100");  
}  
  
ref class G {  
public:  
   int i;  
};  
  
void Test(int % i) {  
   i++;  
}  
  
int main() {  
   G ^ g1 = gcnew G;  
   G ^% g2 = g1;  
   g1 -> i = 12;  
  
   Test(g2->i);   // g2->i will be changed in Test2()  
  
   City ^ Milano = gcnew City(20100);  
   passByRef(Milano);  
}  
```  
  
```Output  
zip == 20100  
```  
  
 Další příklad ukazuje, že adresu sledovací odkaz trvá vrátí [interior_ptr (C + +/ CLI)](../windows/interior-ptr-cpp-cli.md)a ukazuje, jak upravit a přístup k datům prostřednictvím sledovací odkaz.  
  
```cpp  
// tracking_reference_data.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class R {  
public:  
   R(int i) : m_i(i) {  
      Console::WriteLine("ctor: R(int)");  
   }  
  
   int m_i;  
};  
  
class N {  
public:  
   N(int i) : m_i (i) {  
      Console::WriteLine("ctor: N(int i)");  
   }  
  
   int m_i;  
};  
  
int main() {  
   R ^hr = gcnew R('r');  
   R ^%thr = hr;  
   N n('n');  
   N %tn = n;  
  
   // Declare interior pointers  
   interior_ptr<R^> iphr = &thr;  
   interior_ptr<N> ipn = &tn;  
  
   // Modify data through interior pointer  
   (*iphr)->m_i = 1;   // (*iphr)->m_i == thr->m_i  
   ipn->m_i = 4;   // ipn->m_i == tn.m_i  
  
   ++thr-> m_i;   // hr->m_i == thr->m_i  
   ++tn. m_i;   // n.m_i == tn.m_i  
  
   ++hr-> m_i;   // (*iphr)->m_i == hr->m_i  
   ++n. m_i;   // ipn->m_i == n.m_i  
}  
```  
  
```Output  
ctor: R(int)  
ctor: N(int i)  
```  
  
## <a name="tracking-references-and-interior-pointers"></a>Sledování odkazů a vnitřních ukazatelů  
 Následující příklad kódu ukazuje, že můžete převádět mezi sledovacích odkazů a vnitřních ukazatelů.  
  
```cpp  
// tracking_reference_interior_ptr.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class R {  
public:  
   R(int i) : m_i(i) {  
      Console::WriteLine("ctor: R(int)");  
   }  
  
   int m_i;  
};  
  
class N {  
public:  
   N(int i) : m_i(i) {  
      Console::WriteLine("ctor: N(int i)");  
   }  
  
   int m_i;  
};  
  
int main() {  
   R ^hr = gcnew R('r');  
   N n('n');  
  
   R ^%thr = hr;  
   N %tn = n;  
  
   // Declare interior pointers  
   interior_ptr<R^> iphr = &hr;  
   interior_ptr<N> ipn = &n;  
  
   // Modify data through interior pointer  
   (*iphr)->m_i = 1;   // (*iphr)-> m_i == thr->m_i  
   ipn->m_i = 4;   // ipn->m_i == tn.m_i  
  
   ++thr->m_i;   // hr->m_i == thr->m_i  
   ++tn.m_i;   // n.m_i == tn.m_i  
  
   ++hr->m_i;   // (*iphr)->m_i == hr->m_i  
   ++n.m_i;   // ipn->m_i == n.m_i  
}  
```  
  
```Output  
ctor: R(int)  
ctor: N(int i)  
```  
  
## <a name="tracking-references-and-value-types"></a>Sledování odkazů a hodnotových typů  
 Tento příklad ukazuje jednoduchý zabalení prostřednictvím sledovací odkaz na typ hodnoty:  
  
```cpp  
// tracking_reference_valuetypes_1.cpp
// compile with: /clr

using namespace System;

int main() {
   int i = 10;   
   int % j = i;   
   Object ^ o = j;   // j is implicitly boxed and assigned to o
}  
```  
  
 Další příklad ukazuje, že můžete mít sledovacích odkazů a nativní odkazy na typy hodnot.  
  
```cpp  
// tracking_reference_valuetypes_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   int i = 10;  
   int & j = i;  
   int % k = j;  
   i++;   // 11  
   j++;   // 12  
   k++;   // 13  
   Console::WriteLine(i);  
   Console::WriteLine(j);  
   Console::WriteLine(k);  
}  
```  
  
```Output  
13  
13  
13  
```  
  
 Následující příklad ukazuje, které můžete použít společně s nativní typy a hodnoty sledovací odkazy.  
  
```cpp  
// tracking_reference_valuetypes_3.cpp  
// compile with: /clr  
value struct G {  
   int i;  
};  
  
struct H {  
   int i;  
};  
  
int main() {  
   G g;  
   G % v = g;  
   v.i = 4;  
   System::Console::WriteLine(v.i);  
   System::Console::WriteLine(g.i);  
  
   H h;  
   H % w = h;  
   w.i = 5;  
   System::Console::WriteLine(w.i);  
   System::Console::WriteLine(h.i);  
}  
```  
  
```Output  
4  
4  
5  
5  
```  
  
 Tento příklad ukazuje, že lze vázat sledovací odkaz na typ hodnoty v haldě uvolňování paměti:  
  
```cpp  
// tracking_reference_valuetypes_4.cpp  
// compile with: /clr  
using namespace System;  
value struct V {  
   int i;  
};  
  
void Test(V^ hV) {   // hv boxes another copy of original V on GC heap  
   Console::WriteLine("Boxed new copy V: {0}", hV->i);  
}  
  
int main() {  
   V v;   // V on the stack  
   v.i = 1;  
   V ^hV1 = v;   // v is boxed and assigned to hV1  
   v.i = 2;  
   V % trV = *hV1;   // trV is bound to boxed v, the v on the gc heap.  
   Console::WriteLine("Original V: {0}, Tracking reference to boxed V: {1}", v.i, trV.i);  
   V ^hV2 = trV;   // hv2 boxes another copy of boxed v on the GC heap  
   hV2->i = 3;  
   Console::WriteLine("Tracking reference to boxed V: {0}", hV2->i);  
   Test(trV);  
   v.i = 4;  
   V ^% trhV = hV1;  // creates tracking reference to boxed type handle  
   Console::WriteLine("Original V: {0}, Reference to handle of originally boxed V: {1}", v.i, trhV->i);  
}  
```  
  
```Output  
Original V: 2, Tracking reference to boxed V: 1  
Tracking reference to boxed V: 3  
Boxed new copy V: 1  
Original V: 4, Reference to handle of originally boxed V: 1  
```  
  
## <a name="template-functions-that-take-native-value-or-reference-parameters"></a>Šablony funkcí, které přijímají nativní, hodnotu nebo odkaz na parametry  
 Pomocí sledovací odkaz v podpis funkce šablony je zajistit, že funkci nelze volat parametr, jehož typ je nativní, CLR hodnotu nebo odkaz na CLR.  
  
```cpp  
// tracking_reference_template.cpp  
// compile with: /clr  
using namespace System;  
  
class Temp {  
public:  
   // template functions  
   template<typename T>  
   static int f1(T% tt) {   // works for object in any location  
      Console::WriteLine("T %");  
      return 0;  
   }  
  
   template<typename T>  
   static int f2(T& rt) {   // won't work for object on the gc heap  
      Console::WriteLine("T &");  
      return 1;  
   }  
};  
  
// Class Definitions  
ref struct R {  
   int i;  
};  
  
int main() {  
   R ^hr = gcnew R;  
   int i = 1;  
  
   Temp::f1(i); // ok  
   Temp::f1(hr->i); // ok  
   Temp::f2(i); // ok  
  
   // error can't track object on gc heap with a native reference  
   // Temp::f2(hr->i);   
}  
```  
  
```Output  
T %  
T %  
T &  
```  
  
## <a name="see-also"></a>Viz také  
 [Operátor sledovacího odkazu](../windows/tracking-reference-operator-cpp-component-extensions.md)