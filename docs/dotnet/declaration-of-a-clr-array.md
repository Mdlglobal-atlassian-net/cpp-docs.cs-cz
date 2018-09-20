---
title: Deklarace pole CLR | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
ms.assetid: 36a8883c-2663-43f0-a90c-28f27035e036
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c3de17bb293e10c4e1a2287ef12b934633b1fe21
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426455"
---
# <a name="declaration-of-a-clr-array"></a>Deklarace pole CLR

Syntaxe pro deklarování, vytváření instancí a inicializací spravovaného pole změnil ze spravovaného rozšíření jazyka C++ na Visual C++.

Deklarace pole objektu CLR do spravovaného rozšíření se rozšíření deklarace standardní pole, ve kterém `__gc` – klíčové slovo byl umístěn mezi název pole objektu a jeho dimenze může být vyplněny čárkami, stejně jako v následující dvojice Příklady:

```
void PrintValues( Object* myArr __gc[]);
void PrintValues( int myArr __gc[,,]);
```

To bylo zjednodušeno v nové syntaxi, ve kterém používáme deklaraci šablony jako podobně jako standardní knihovny C++ `vector` deklarace. První parametr určuje typ elementu. Druhý parametr určuje rozměry pole (s výchozí hodnotou 1, vyžadují druhý argument pouze více dimenzí). Samotného objektu array je sledovací popisovač a proto musí být uvedeny stříška. Pokud typ prvku i typu odkaz, vyžaduje také stříška. Například výše uvedeném příkladu vyjádřené v nové syntaxi, vypadá takto:

```
void PrintValues( array<Object^>^ myArr );
void PrintValues( array<int,3>^ myArr );
```

Protože typ odkazu je sledovací popisovač, nikoli objekt, je možné zadat pole CLR jako návratový typ funkce. (Oproti tomu není možné zadat nativní pole jako návratový typ funkce.) Tím ve spravovaných rozšíření syntaxe se poněkud neintuitivní. Příklad:

```
Int32 f() [];
int GetArray() __gc[];
```

V jazyce Visual C++ je mnohem jednodušší deklarace. Například

```
array<Int32>^ f();
array<int>^ GetArray();
```

Zkrácený tvar vlastností inicializace místní spravovaného pole je podporován v obou verzích tohoto jazyka. Příklad:

```
int GetArray() __gc[] {
   int a1 __gc[] = { 1, 2, 3, 4, 5 };
   Object* myObjArray __gc[] = {
      __box(26), __box(27), __box(28), __box(29), __box(30)
   };
   return a1;
}
```

je výrazně zjednodušené v nové syntaxi (Upozorňujeme, že zabalení je implicitní v nové syntaxi `__box` odstraněn operátor – viz [typy hodnot a jejich chování (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md) diskuzi):

```
array<int>^ GetArray() {
   array<int>^ a1 = {1,2,3,4,5};
   array<Object^>^ myObjArray = {26,27,28,29,30};
   return a1;
}
```

Vzhledem k tomu, že pole je odkaz na typ CLR, deklarace od každého objektu array je sledovací popisovač. Proto musí být přiděleny pole objektů na haldě modulu CLR. (Zjednodušenou notaci skryje spravované haldy.) Tady je explicitní forma inicializace objektu pole v rámci spravovaného rozšíření:

```
Object* myArray[] = new Object*[2];
String* myMat[,] = new String*[4,4];
```

V nové syntaxi `new` výraz se nahradí `gcnew`. Velikosti dimenze jsou předány jako parametry `gcnew` výraz následujícím způsobem:

```
array<Object^>^ myArray = gcnew array<Object^>(2);
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);
```

V nové syntaxi, můžete použít explicitní inicializační seznam `gcnew` výrazu; to není podporováno ve spravovaných rozšíření. Příklad:

```
// explicit initialization list following gcnew
// was not supported in Managed Extensions
array<Object^>^ myArray =
   gcnew array<Object^>(4){ 1, 1, 2, 3 };
```

## <a name="see-also"></a>Viz také

[Spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Pole](../windows/arrays-cpp-component-extensions.md)