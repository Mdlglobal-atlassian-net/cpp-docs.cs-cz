---
title: Obecné funkce (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
ms.openlocfilehash: a4a1702c8b9902f5265a8a5f92316d7c82751609
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038700"
---
# <a name="generic-functions-ccli"></a>Obecné funkce (C++/CLI)

Obecné funkce je funkce, která je deklarována s parametry typu. Při volání skutečné typy používané místo parametry typu.

## <a name="all-platforms"></a>Všechny platformy

### <a name="remarks"></a>Poznámky

Tato funkce se nevztahují na všechny platformy.

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="remarks"></a>Poznámky

Tato funkce není podporována v modulu Windows Runtime.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Obecné funkce je funkce, která je deklarována s parametry typu. Při volání skutečné typy používané místo parametry typu.

### <a name="syntax"></a>Syntaxe

```cpp
[attributes] [modifiers]
return-type identifier<type-parameter identifier(s)>
[type-parameter-constraints clauses]

([formal-parameters])
{function-body}
```

### <a name="parameters"></a>Parametry

*atributy*<br/>
(Volitelné) Další informace o deklarativní. Další informace o atributu třídy a atributy naleznete v tématu atributy.

*modifikátory*<br/>
(Volitelné) Modifikátor pro funkce, jako je statická.  **virtuální** není povolená, protože virtuální metody nemusí být obecný.

*Návratový typ*<br/>
Typ vrácený metodou Pokud je návratový typ void, vyžádáním žádnou návratovou hodnotu.

*identifikátor*<br/>
Název funkce.

*parametr typu identifikátory*<br/>
Seznam identifikátorů oddělených čárkou.

*formální parametry*<br/>
(Volitelné) Seznam parametrů.

*type-parameter-constraints-clauses*<br/>
Toto určuje omezení na typy, které mohou používat jako argumenty typu a má podobu podle [omezení parametrů obecných typů (C + +/ CLI)](constraints-on-generic-type-parameters-cpp-cli.md).

*tělo funkce*<br/>
Tělo metody, která mohou odkazovat na identifikátory parametr typu.

### <a name="remarks"></a>Poznámky

Obecné funkce jsou funkce deklarované s parametr obecného typu. Mohou být metody do třídy nebo struktury nebo samostatné funkce. Jeden obecný deklarace implicitně deklaruje název řady funkcí, které se liší pouze v rámci nahrazování jiný typ skutečného parametru obecného typu.

Konstruktor třídy nebo struktury nemůže být deklarovaný s parametry obecného typu.

Při volání, parametr obecného typu je nahrazen skutečným typem. Skutečný typ může být explicitně zadán v ostrými závorkami pomocí syntaxe podobné volání šablony funkce. Pokud je volána bez parametrů typu, kompilátor se pokusí odvodit skutečný typ z parametry zadané ve volání funkce. Pokud argumentu zamýšlený typ nelze odvodit z parametrů použitých, kompilátor oznámí chybu.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující vzorový kód ukazuje obecnou funkci.

```cpp
// generics_generic_function_1.cpp
// compile with: /clr
generic <typename ItemType>
void G(int i) {}

ref struct A {
   generic <typename ItemType>
   void G(ItemType) {}

   generic <typename ItemType>
   static void H(int i) {}
};

int main() {
   A myObject;

   // generic function call
   myObject.G<int>(10);

   // generic function call with type parameters deduced
   myObject.G(10);

   // static generic function call
   A::H<int>(10);

   // global generic function call
   G<int>(10);
}
```

Obecné funkce mohou být přetíženy podle podpis nebo Arita, počet parametrů typu na funkci. Obecné funkce také mohou být přetíženy s neobecné funkce se stejným názvem, tak dlouho, dokud funkce se liší v některé parametry typu. Například mohou být přetíženy následující funkce:

```cpp
// generics_generic_function_2.cpp
// compile with: /clr /c
ref struct MyClass {
   void MyMythod(int i) {}

   generic <class T>
   void MyMythod(int i) {}

   generic <class T, class V>
   void MyMythod(int i) {}
};
```

V následujícím příkladu používá obecná funkce k vyhledání prvního prvku v poli. Deklaruje `MyClass`, který dědí ze základní třídy `MyBaseClass`. `MyClass` obsahuje obecná funkce `MyFunction`, která volá jinou funkci Obecné, `MyBaseClassFunction`, v rámci základní třídy. V `main`, obecná funkce `MyFunction`, je volána pomocí jiného typu argumentů.

```cpp
// generics_generic_function_3.cpp
// compile with: /clr
using namespace System;

ref class MyBaseClass {
protected:
   generic <class ItemType>
   ItemType MyBaseClassFunction(ItemType item) {
      return item;
   }
};

ref class MyClass: public MyBaseClass {
public:
   generic <class ItemType>
   ItemType MyFunction(ItemType item) {
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);
   }
};

int main() {
   MyClass^ myObj = gcnew MyClass();

   // Call MyFunction using an int.
   Console::WriteLine("My function returned an int: {0}",
                           myObj->MyFunction<int>(2003));

   // Call MyFunction using a string.
   Console::WriteLine("My function returned a string: {0}",
   myObj->MyFunction<String^>("Hello generic functions!"));
}
```

```Output
My function returned an int: 2003
My function returned a string: Hello generic functions!
```

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)<br/>
[Obecné typy](generics-cpp-component-extensions.md)
