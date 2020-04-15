---
title: Operátor popisovače objektu (^) (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- ^ handle to object [C++]
ms.assetid: 70c411e6-be57-4468-a944-6ea7be89f392
ms.openlocfilehash: 3d08b2294da1599282feeb1739331c31d64a9e59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358334"
---
# <a name="handle-to-object-operator---ccli-and-ccx"></a>Operátor popisovače objektu (^) (C++/CLI a C++/CX)

*Deklarátor popisovače* (`^`, vyslovuje "hat"), upraví [specifikátor](../cpp/overview-of-declarators.md) typu tak, že deklarovaný objekt by měl být automaticky odstraněn, když systém určí, že objekt již není přístupný.

## <a name="accessing-the-declared-object"></a>Přístup k deklarovanému objektu

Proměnná, která je deklarována s deklarátorem popisovače, se chová jako ukazatel na objekt. Proměnná však odkazuje na celý objekt, nemůže ukázat na člen objektu a nepodporuje aritmetiku ukazatele. Pomocí operátoru dereference (`*`) pro přístup k objektu`->`a operátor přístupu člena šipky ( ) pro přístup k členu objektu.

## <a name="windows-runtime"></a>prostředí Windows Runtime

Kompilátor používá mechanismus *počítání odkazů* COM k určení, zda se objekt již nepoužívá a může být odstraněn. To je možné, protože objekt, který je odvozen z rozhraní prostředí Windows Runtime je ve skutečnosti objekt COM. Počet odkazů se zvětší při vytvoření nebo zkopírování objektu a sníží, když je objekt nastaven na hodnotu null nebo přejde mimo rozsah. Pokud počet odkazů přejde na nulu, objekt je automaticky a okamžitě odstraněn.

Výhodou deklarátoru popisovače je, že v com musíte explicitně spravovat počet odkazů pro objekt, což je zdlouhavý proces náchylný k chybám. To znamená zvýšit a zmenšit počet odkazů, musíte volat metody AddRef() a Release() objektu. Pokud však deklarujete objekt s deklarátorem popisovače, kompilátor vygeneruje kód, který automaticky upraví počet odkazů.

Informace o vytvoření instance objektu naleznete v [tématu ref new](ref-new-gcnew-cpp-component-extensions.md).

## <a name="requirements"></a>Požadavky

Možnost kompilátoru:`/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Systém používá clr *mechanismus uvolňování paměti* k určení, pokud objekt již používá a lze odstranit. Běžný jazyk runtime udržuje haldu, na které přiděluje objekty a používá spravované odkazy (proměnné) v programu označují umístění objektů na haldě. Pokud objekt již není používán, je uvolněna paměť, kterou obsazuje na haldě. Pravidelně uvolňování zhutní haldy lépe využít uvolněnou paměť. Komprimace haldy můžete přesunout objekty na haldě, která zruší platnost umístění odkazuje spravované odkazy. Systém uvolňování paměti si však uvědomuje umístění všech spravovaných odkazů a automaticky je aktualizuje, aby označil aktuální umístění objektů na haldě.

Vzhledem k tomu,`*`že nativní`&`ukazatele jazyka C++ ( ) a odkazy ( ) nejsou spravované odkazy, systém uvolňování paměti nemůže automaticky aktualizovat adresy, na které odkazují. Chcete-li tento problém vyřešit, použijte deklarátor popisovače k určení proměnné, která systém uvolňování paměti je vědoma a může aktualizovat automaticky.

Další informace naleznete v [tématu How to: Declare handles in Native Types](../dotnet/how-to-declare-handles-in-native-types.md).

### <a name="examples"></a>Příklady

Tato ukázka ukazuje, jak vytvořit instanci typu odkazu na spravované haldy.  Tato ukázka také ukazuje, že můžete inicializovat jeden popisovač s jiným, výsledkem jsou dva odkazy na stejný objekt na spravované haldě s uvolňováním paměti. Všimněte si, že přiřazení [nullptr](nullptr-cpp-component-extensions.md) jednomu popisovači neoznačuje objekt pro uvolnění paměti.

```cpp
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

```Output
1
2
```

Následující ukázka ukazuje, jak deklarovat popisovač objektu na spravované haldě, kde typ objektu je zabalený typ hodnoty. Ukázka také ukazuje, jak získat typ hodnoty z krabicového objektu.

```cpp
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

```Output
Not a boxed int
100
```

Tato ukázka ukazuje, že společný idiom `void*` jazyka C++ použití ukazatele pro `Object^`odkaz na libovolný objekt je nahrazen o , který může obsahovat popisovač pro libovolnou referenční třídu. Také ukazuje, že všechny typy, jako jsou pole a delegáti, lze převést na popisovač objektu.

```cpp
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

```Output
Type is System.Collections.ArrayList

Type is System.Int32

Type is MyDel
```

Tato ukázka ukazuje, že popisovač může být odkazováno a že člen lze přistupovat prostřednictvím popisovač dereferenced.

```cpp
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

```Output
Array value: 7

Cannot access array element 11, size is 10
```

Tato ukázka ukazuje,`&`že nativní odkaz ( ) nelze vázat **na int** člen spravovaného typu, jako **int** může být uloženv haldě uvolněné a nativní odkazy nesledují pohyb objektu ve spravované haldy. Oprava je použití místní proměnné nebo `&` změnit `%`na , takže je odkaz na sledování.

```cpp
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

Možnost kompilátoru:`/clr`

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)<br/>
[Operátor sledovacího odkazu](tracking-reference-operator-cpp-component-extensions.md)
