---
title: Obecní delegátiC++(/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
ms.openlocfilehash: 4c579d0c0ab39a2ddcadfd116bdfed8ba9da2863
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182029"
---
# <a name="generic-delegates-ccli"></a>Obecní delegátiC++(/CLI)

Parametry obecného typu můžete použít s delegáty. Další informace o delegátech naleznete v tématu [DelegateC++(/CLI C++a/CX)](delegate-cpp-component-extensions.md).

## <a name="syntax"></a>Syntaxe

```cpp
[attributes]
generic < [class | typename] type-parameter-identifiers>
[type-parameter-constraints-clauses]
[accessibility-modifiers] delegate result-type identifier
([formal-parameters]);
```

### <a name="parameters"></a>Parametry

*atribut*<br/>
Volitelné Další deklarativní informace. Další informace o atributech a třídách atributů naleznete v tématu Attributes.

*typ – identifikátory parametrů:*<br/>
Čárkami oddělený seznam identifikátorů pro parametry typu.

*Type-Parameter-Constraints – klauzule*<br/>
Převezme formulář zadaný v [omezeních parametrů obecného typu (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md) .

*usnadnění – modifikátory*<br/>
Volitelné Modifikátory dostupnosti (například **Public**, **Private**).

*Typ výsledku*<br/>
Návratový typ delegáta.

*RID*<br/>
Název delegáta.

*formální parametry*<br/>
Volitelné Seznam parametrů delegáta.

## <a name="example"></a>Příklad

Parametry typu delegáta jsou zadány v místě, kde je vytvořen objekt delegát. Delegát i metoda, ke kterým je přidružená, musí mít stejnou signaturu. Následuje příklad deklarace obecného delegáta.

```cpp
// generics_generic_delegate1.cpp
// compile with: /clr /c
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, že

- Nemůžete použít stejný objekt delegáta s různými konstruovanými typy. Vytvoření různých objektů delegátů pro různé typy.

- Obecný delegát může být přidružen k obecné metodě.

- Když je obecná metoda volána bez určení argumentů typu, kompilátor se pokusí odvodit argumenty typu pro volání.

```cpp
// generics_generic_delegate2.cpp
// compile with: /clr
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);

generic <class ItemType>
ref struct MyGenClass {
   ItemType MyMethod(ItemType i, ItemType % j) {
      return ItemType();
   }
};

ref struct MyClass {
   generic <class ItemType>
   static ItemType MyStaticMethod(ItemType i, ItemType % j) {
      return ItemType();
   }
};

int main() {
   MyGenClass<int> ^ myObj1 = gcnew MyGenClass<int>();
   MyGenClass<double> ^ myObj2 = gcnew MyGenClass<double>();
   GenDelegate<int>^ myDelegate1 =
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);

   GenDelegate<double>^ myDelegate2 =
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);

   GenDelegate<int>^ myDelegate =
      gcnew GenDelegate<int>(&MyClass::MyStaticMethod<int>);
}
```

## <a name="example"></a>Příklad

Následující příklad deklaruje generický delegáta `GenDelegate<ItemType>`a poté vytvoří instanci tak, že ji přidruží k metodě `MyMethod`, která používá parametr typu `ItemType`. Vytvoří a vyvolají se dvě instance delegáta (celočíselná a Dvojitá).

```cpp
// generics_generic_delegate.cpp
// compile with: /clr
using namespace System;

// declare generic delegate
generic <typename ItemType>
delegate ItemType GenDelegate (ItemType p1, ItemType% p2);

// Declare a generic class:
generic <typename ItemType>
ref class MyGenClass {
public:
   ItemType MyMethod(ItemType p1, ItemType% p2) {
      p2 = p1;
      return p1;
    }
};

int main() {
   int i = 0, j = 0;
   double m = 0.0, n = 0.0;

   MyGenClass<int>^ myObj1 = gcnew MyGenClass<int>();
   MyGenClass<double>^ myObj2 = gcnew MyGenClass<double>();

   // Instantiate a delegate using int.
   GenDelegate<int>^ MyDelegate1 =
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);

   // Invoke the integer delegate using MyMethod.
   i = MyDelegate1(123, j);

   Console::WriteLine(
      "Invoking the integer delegate: i = {0}, j = {1}", i, j);

   // Instantiate a delegate using double.
   GenDelegate<double>^ MyDelegate2 =
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);

   // Invoke the integer delegate using MyMethod.
   m = MyDelegate2(0.123, n);

   Console::WriteLine(
      "Invoking the double delegate: m = {0}, n = {1}", m, n);
}
```

```Output
Invoking the integer delegate: i = 123, j = 123
Invoking the double delegate: m = 0.123, n = 0.123
```

## <a name="see-also"></a>Viz také

[Obecné typy](generics-cpp-component-extensions.md)
