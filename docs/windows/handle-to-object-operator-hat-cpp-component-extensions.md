---
title: Operátor popisovače objektu (^) (C + +/ CLI a C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ^ handle to object [C++]
ms.assetid: 70c411e6-be57-4468-a944-6ea7be89f392
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5fe5bf67df643f83d555d3f2d6fc9a0aadf84b01
ms.sourcegitcommit: 68cd127a6606f0aed2eb1bc9a75cdfb95b9b6526
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204887"
---
# <a name="handle-to-object-operator---ccli-and-ccx"></a>Operátor popisovače objektu (^) (C + +/ CLI a C + +/ CX)

*Deklarátor popisovače* (`^`, výslovnost "stříška"), změní typ [specifikátor](../cpp/overview-of-declarators.md) znamenat, že deklarovaný objekt má být automaticky odstraněn, když systém zjistí, že objekt je už nebude přístupný.

## <a name="accessing-the-declared-object"></a>Přístup k deklarovanému objektu

Proměnná, která je deklarována pomocí deklarátoru popisovače se chová jako ukazatel na objekt. Ale proměnná odkazuje na celý objekt a nemůže odkazovat na člena objektu a nepodporuje aritmetiku ukazatele. Použití operátoru dereference (`*`) pro přístup k objektu a šipku operátora přístupu členů (`->`) pro přístup ke členu objektu.

## <a name="windows-runtime"></a>prostředí Windows Runtime

Kompilátor používá COM *počítání odkazů* mechanismus pro určení, zda objekt se už nepoužívá a je možné odstranit. To je možné, protože objekt, který je odvozen z rozhraní Windows Runtime je ve skutečnosti objekt modelu COM. Počet odkazů je zvýšen, pokud je objekt vytvořený nebo zkopírován a snížen, když je objekt nastaven na hodnotu null nebo přejde mimo obor. Pokud počet odkazů dosáhne nuly, objekt je automaticky a okamžitě odstraněn.

Výhodou deklarátoru popisovač je, že v COM musíte explicitně spravovat počet odkazů pro objekt, což je únavné a snadno dojde k chybám proces. To znamená a zvýší počet odkazů musí volat metody zvýšit a Release() objektu. Nicméně pokud deklarujete objekt s deklarátorem popisovače, kompilátor generuje kód, který automaticky přizpůsobí počet odkazů.

Informace o tom, jak vytvořit instanci objektu naleznete v tématu [ref nové](../windows/ref-new-gcnew-cpp-component-extensions.md).

## <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Systém používá modul CLR *systému uvolňování paměti* mechanismus pro určení, zda objekt se už nepoužívá a je možné odstranit. Modul common language runtime udržuje haldu, na které se přidělují objekty a používá spravované odkazy (proměnné) ve svém programu označení umístění objektů na haldě. Pokud objekt už nebude používat, je uvolněna paměť, která je obsazena na haldě. Pravidelně systému uvolňování paměti zkomprimuje hladu k lepšímu využití uvolněné paměti. Komprimací haldy můžete přesunout objekty do haldy, čímž zrušíte platnost umístění uváděná spravovanými odkazy uvedené. Ale systému uvolňování paměti zná umístění všech spravovaných odkazů a automaticky je aktualizuje pro označení aktuálního umístění objektů na haldě.

Protože nativní ukazatelé C++ (`*`) a odkazy (`&`) nejsou spravované odkazy, uvolňování nemůže automaticky aktualizovat adresy, které ukazují na. Pokud chcete tento problém vyřešit, použijte deklarátor popisovače k určení proměnné, které systému uvolňování paměti je vědět a lze ji automaticky aktualizovat.

Další informace najdete v tématu [postupy: deklarování zpracovává v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md).

### <a name="examples"></a>Příklady

Tento příklad ukazuje, jak vytvořit instanci typu odkazu na spravované haldě.  Tento příklad také ukazuje, že inicializace jednoho popisovače jiným vytvoří dva odkazy na stejný objekt na spravované, uvolnění paměti haldy. Všimněte si, že přiřazení [nullptr](../windows/nullptr-cpp-component-extensions.md) k popisovači neoznačí objekt pro uvolňování paměti.

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

Následující příklad ukazuje, jak deklarovat popisovač pro objekt na spravované haldě, kde typ objektu je zabalený typ hodnoty. Ukázka také ukazuje, jak získat typ hodnoty ze zabaleného objektu.

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

Tento příklad ukazuje, že běžný idiom C++ používání `void*` ukazatel na libovolný objekt je nahrazen `Object^`, který může obsahovat popisovač na referenční třídu. Profil také ukazuje, že všechny typy, jako jsou pole a delegáty, mohou být převedeny na popisovač objektu.

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

Tento příklad ukazuje, že popisovač může být dereferencován a že člen je přístupný pomocí dereferencovaného popisovače.

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

Tento příklad ukazuje, že nativní odkaz (`&`) nelze vytvořit vazbu **int** člen spravovaného typu, jako **int** můžou být uložená v haldě uvolňování paměti a nativní odkazy nesledují pohyb objektu ve spravované haldě. Opravou je použití místní proměnné nebo změna `&` k `%`, takže odkazem sledování.

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

– Možnost kompilátoru: `/clr`

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](../windows/component-extensions-for-runtime-platforms.md)<br/>
[Operátor sledovacího odkazu](../windows/tracking-reference-operator-cpp-component-extensions.md)
