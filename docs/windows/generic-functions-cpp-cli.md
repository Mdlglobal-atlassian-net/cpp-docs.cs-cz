---
title: Obecné funkce (C + +/ CLI) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bc930fdc142dc7b044b4dbd60cfd459b7ce52aea
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709140"
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

*Atributy*  
(Volitelné) Další informace o deklarativní. Další informace o atributu třídy a atributy naleznete v tématu atributy.

*Modifikátory*  
(Volitelné) Modifikátor pro funkce, jako je statická.  **virtuální** není povolená, protože virtuální metody nemusí být obecný.

*Návratový typ*  
Typ vrácený metodou Pokud je návratový typ void, vyžádáním žádnou návratovou hodnotu.

*identifikátor*  
Název funkce.

*parametr typu identifikátory*  
Seznam identifikátorů oddělených čárkou.

*formální parametry*  
(Volitelné) Seznam parametrů.

*Typ parametru omezení klauzule*  
Toto určuje omezení na typy, které mohou používat jako argumenty typu a má podobu podle [omezení parametrů obecných typů (C + +/ CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md).

*tělo funkce*  
Tělo metody, která mohou odkazovat na identifikátory parametr typu.

### <a name="remarks"></a>Poznámky

Obecné funkce jsou funkce deklarované s parametr obecného typu. Mohou být metody do třídy nebo struktury nebo samostatné funkce. Jeden obecný deklarace implicitně deklaruje název řady funkcí, které se liší pouze v rámci nahrazování jiný typ skutečného parametru obecného typu.

V jazyce Visual C++ nemůže být deklarovaný třídy nebo struktury konstruktory s parametry obecného typu.

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

## <a name="see-also"></a>Viz také

[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)  
[Obecné typy](../windows/generics-cpp-component-extensions.md)