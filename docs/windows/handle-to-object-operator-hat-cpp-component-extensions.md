---
title: "Operátor popisovače objektu (^) (C++ Component Extensions) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- ^ handle to object [C++]
ms.assetid: 70c411e6-be57-4468-a944-6ea7be89f392
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e760181f48e4bfd197514b152701e94ac6e94a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="handle-to-object-operator---c-component-extensions"></a>Operátor popisovače objektu (^) (rozšíření komponent C++)
*Zpracování deklarátor* (`^`, vyslovováno "hat"), upraví typ [specifikátor](../cpp/overview-of-declarators.md) znamená, že objekt deklarované měla by být automaticky odstraněna, když systém zjistí, že objekt již nebudou dostupné.  
  
## <a name="accessing-the-declared-object"></a>Přístup deklarované objektu  
 Proměnné, která je deklarovaný s popisovačem deklarátor se chová jako ukazatel na objekt. Ale proměnné odkazuje na celý objekt nemůže odkazovat na člen objektu a nepodporuje aritmetika ukazatele. Deferenční operátor (`*`) pro přístup k objektu a operátor šipku přístup ke členu (`->`) pro přístup ke členu objektu.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Kompilátor používá modelu COM *počítání odkazů* mechanismus k určení, pokud objekt je již používán a lze je odstranit. To je možné, protože objekt, který je odvozený z prostředí Windows Runtime rozhraní je ve skutečnosti objekt COM. Počet odkazů se zvýší, když je objekt vytvořený nebo zkopírované a odečte objektu je nastavena na hodnotu null nebo přejde mimo rozsah. Pokud počet odkazů přejde na hodnotu nula, objekt je automaticky a okamžitě odstranit.  
  
 Výhodou deklarátor popisovač je v modelu COM musí explicitně spravovat počet odkazů pro objekt, což je proces náchylné k chybám zdlouhavé a chyby. To znamená zvýší a sníží počet odkazů musí volat metody AddRef() a Release() objektu. Ale pokud je objekt deklarovat s deklarátor popisovač, Visual C++ compiler generuje kód, který automaticky přizpůsobí počet odkazů.  
  
 Informace o tom, jak vytvořit instanci objektu najdete v tématu [ref nové](../windows/ref-new-gcnew-cpp-component-extensions.md).  
  
## <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 Modul CLR používá systém *systém uvolňování paměti* mechanismus k určení, pokud objekt je již používán a lze je odstranit. Modul common language runtime udržuje haldy, na kterém přiděluje objekty a používá spravované odkazy (proměnné) v programu uveďte umístění objektů v haldě. Pokud objekt se už používá, je uvolnit paměť, který je zaneprázdněn v haldě. Pravidelně uvolňování zkomprimuje haldě k lepšímu využití uvolněné paměti. Kompresi halda můžete přesunout objekty v haldě, která by způsobila neplatnost umístění uvedená ve spravovaných odkazy. Ale uvolňování si je vědoma umístění všechny odkazy na spravovaných a automaticky aktualizuje je aktuální umístění objektů v haldě označuje.  
  
 Protože nativními ukazateli C++ (`*`) a odkazy (`&`) nejsou spravované odkazy, bude systém uvolňování nemůže aktualizovat automaticky adresy ukazovaly na. Chcete-li tento problém vyřešit, pomocí deklarátor popisovač určete proměnné, která je bude systém uvolňování paměti a můžete aktualizovat automaticky.  
  
 Ve Visual C++ 2002 a Visual C++ 2003 `__gc *` byla použita k deklarace objektu na spravované haldě.  `^` Nahrazuje `__gc *` v nové syntaxe.  
  
 Další informace najdete v tématu [postupy: deklarace zpracovává v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md).  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Tento příklad ukazuje, jak vytvořit instanci typu odkazu na spravovaná halda.  Tento příklad také ukazuje, že inicializovat jeden popisovač s jinou, výsledkem dva odkazy na stejný objekt na haldě spravovaná, uvolňování paměti. Všimněte si, že přiřazení [nullptr](../windows/nullptr-cpp-component-extensions.md) do jednoho popisovače neoznačí objekt pro uvolňování paměti.  
  
```  
// mcppv2_handle.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   MyClass() : i(){}  
   int i;  
   void Test() {  
      i++;  
      System::Console::WriteLine(i);  
   }  
};  
  
int main() {  
   MyClass ^ p_MyClass = gcnew MyClass;  
   p_MyClass->Test();  
  
   MyClass ^ p_MyClass2;  
   p_MyClass2 = p_MyClass;  
  
   p_MyClass = nullptr;  
   p_MyClass2->Test();     
}  
```  
  
 **Output**  
  
```Output  
1  
2  
```  
  
 **Příklad**  
  
 Následující příklad ukazuje, jak na spravovaná halda, kde je typ objektu typu zabalené hodnoty deklarovat popisovač pro objekt. Ukázka také ukazuje, jak získat typ hodnoty z zabalené objektu.  
  
```  
// mcppv2_handle_2.cpp  
// compile with: /clr  
using namespace System;  
  
void Test(Object^ o) {  
   Int32^ i = dynamic_cast<Int32^>(o);  
  
   if(i)  
      Console::WriteLine(i);  
   else  
      Console::WriteLine("Not a boxed int");  
}  
  
int main() {  
   String^ str = "test";  
   Test(str);  
  
   int n = 100;  
   Test(n);  
}  
```  
  
 **Output**  
  
```Output  
Not a boxed int  
100  
```  
  
 **Příklad**  
  
 Tento příklad ukazuje běžné stylu C++ pomocí ukazatel void * tak, aby odkazoval na libovolný objekt je nahrazena objekt ^, které mohou být uloženy popisovač pro všechny referenční třídy. Také ukazuje, že všechny typy, jako je například pole a delegáti, můžete převést na popisovač objektu.  
  
```  
// mcppv2_handle_3.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Collections;  
public delegate void MyDel();  
ref class MyClass {  
public:  
   void Test() {}  
};  
  
void Test(Object ^ x) {  
   Console::WriteLine("Type is {0}", x->GetType());  
}  
  
int main() {  
   // handle to Object can hold any ref type  
   Object ^ h_MyClass = gcnew MyClass;  
  
   ArrayList ^ arr = gcnew ArrayList();  
   arr->Add(gcnew MyClass);  
  
   h_MyClass = dynamic_cast<MyClass ^>(arr[0]);  
   Test(arr);  
  
   Int32 ^ bi = 1;  
   Test(bi);  
  
   MyClass ^ h_MyClass2 = gcnew MyClass;  
  
   MyDel^ DelInst = gcnew MyDel(h_MyClass2, &MyClass::Test);  
   Test(DelInst);  
}  
```  
  
 **Output**  
  
```Output  
Type is System.Collections.ArrayList  
  
Type is System.Int32  
  
Type is MyDel  
```  
  
 **Příklad**  
  
 Tento příklad ukazuje, že můžete přímo odkázat popisovač a že členem je přístupná prostřednictvím dereferenced popisovač.  
  
```  
// mcppv2_handle_4.cpp  
// compile with: /clr  
using namespace System;  
value struct DataCollection {  
private:  
   int Size;  
   array<String^>^ x;  
  
public:  
   DataCollection(int i) : Size(i) {  
      x = gcnew array<String^>(Size);  
      for (int i = 0 ; i < Size ; i++)  
         x[i] = i.ToString();  
   }  
  
   void f(int Item) {  
      if (Item >= Size)  
      {  
         System::Console::WriteLine("Cannot access array element {0}, size is {1}", Item, Size);  
         return;  
      }  
      else  
         System::Console::WriteLine("Array value: {0}", x[Item]);  
   }  
};  
  
void f(DataCollection y, int Item) {  
   y.f(Item);  
}  
  
int main() {  
   DataCollection ^ a = gcnew DataCollection(10);  
   f(*a, 7);   // dereference a handle, return handle's object  
   (*a).f(11);   // access member via dereferenced handle  
}  
```  
  
 **Output**  
  
```Output  
Array value: 7  
  
Cannot access array element 11, size is 10  
```  
  
 **Příklad**  
  
 Tento příklad ukazuje, že nativní referenční dokumentace (`&`) nelze vytvořit vazbu na `int` člen spravovaného typu, jako `int` se pravděpodobně uloží do shromážděných halda paměti a nativní odkazy nemáte sledují pohyb objektů v spravovaná halda. Oprava je místní proměnné, nebo chcete-li změnit `&` k `%`, což sledovací odkaz.  
  
```  
// mcppv2_handle_5.cpp  
// compile with: /clr  
ref struct A {  
   void Test(unsigned int &){}  
   void Test2(unsigned int %){}  
   unsigned int i;  
};  
  
int main() {  
   A a;  
   a.i = 9;  
   a.Test(a.i);   // C2664  
   a.Test2(a.i);   // OK  
  
   unsigned int j = 0;  
   a.Test(j);   // OK  
}  
```  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)   
 [Operátor sledovacího odkazu](../windows/tracking-reference-operator-cpp-component-extensions.md)