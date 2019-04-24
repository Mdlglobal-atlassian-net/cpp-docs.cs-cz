---
title: Obecní delegáti (C++vyhodnocovací)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
ms.openlocfilehash: 449659126f52997d548ebd7785a78c1200038ee6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62254927"
---
# <a name="generic-delegates-ccli"></a>Obecní delegáti (C++vyhodnocovací)

Můžete použít parametry obecného typu pomocí delegátů. Další informace o delegátech naleznete v tématu [delegáta (C++vyhodnocovací a C++/CX)](delegate-cpp-component-extensions.md).

## <a name="syntax"></a>Syntaxe

```cpp
[attributes]
generic < [class | typename] type-parameter-identifiers>
[type-parameter-constraints-clauses]
[accessibility-modifiers] delegate result-type identifier
([formal-parameters]);
```

### <a name="parameters"></a>Parametry

*Atributy*<br/>
(Volitelné) Další informace o deklarativní. Další informace o atributu třídy a atributy naleznete v tématu atributy.

*Typ – parametr-identifikátory*<br/>
Čárkou oddělený seznam identifikátorů pro parametry typu.

*type-parameter-constraints-clauses*<br/>
Má podobu podle [omezení parametrů obecných typů (C++vyhodnocovací)](constraints-on-generic-type-parameters-cpp-cli.md)

*accessibility-modifiers*<br/>
(Volitelné) Modifikátory (třeba **veřejné**, **privátní**).

*Typ výsledku*<br/>
Návratový typ delegáta.

*identifier*<br/>
Název delegáta.

*formální parametry*<br/>
(Volitelné) Seznam parametrů delegáta.

## <a name="example"></a>Příklad

V okamžiku, kdy je vytvořen objekt delegáta jsou zadány parametry typu delegát. Delegáta a přidružená metoda musí mít stejný podpis. Následuje příklad deklarace obecného delegáta.

```cpp
// generics_generic_delegate1.cpp
// compile with: /clr /c
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, že

- Stejný objekt delegáta nelze použít s různými typy vytvořený. Vytvořte různé delegáta pro různé typy objektů.

- Obecný delegát může být spojeny s obecnou metodou.

- Při volání obecné metody bez zadání argumentů, kompilátor se pokusí odvodit argumenty typu pro volání.

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

Následující příklad deklaruje obecného delegátu `GenDelegate<ItemType>`a poté vytvoří instanci tím, že přidružíte k metodě `MyMethod` , která používá parametr typu `ItemType`. Dvě instance delegáta (celé číslo a typ double) jsou vytvořena a vyvolána.

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

## <a name="see-also"></a>Viz také:

[Obecné typy](generics-cpp-component-extensions.md)