---
title: Deklarace spravovaného typu třídy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- classes [C++], managed
- class keyword [C++], CLR
- __value keyword
- value types, declaring
- value keyword [C++]
- managed classes
- interface class keyword
- ref keyword [C++]
ms.assetid: 16de9c94-91d7-492f-8ac7-f0729cc627e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0f9ceb0867fbdfbbdb46075662fca802d1ee0bba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393669"
---
# <a name="declaration-of-a-managed-class-type"></a>Deklarace spravovaného typu třídy

Způsob, jak deklarovat typ referenční třídy změněn ze spravovaného rozšíření jazyka C++ pro Visual C++.

Ve spravovaných rozšíření typu referenční třídy začíná `__gc` – klíčové slovo. V nové syntaxi `__gc` – klíčové slovo je nahrazena jednu ze dvou rozložených klíčových slov: `ref class` nebo `ref struct`. Volba `struct` nebo `class` označuje veřejnou (pro `struct`) nebo soukromých (pro `class`) výchozí úroveň přístupu z jejích členů deklarované v počáteční samostatná část obsahu typu.

Podobně ve spravovaných rozšíření, je hodnota typu třídy začíná `__value` – klíčové slovo. V nové syntaxi `__value` – klíčové slovo je nahrazena jednu ze dvou rozložených klíčových slov: `value class` nebo `value struct`.

Typ rozhraní v rozšířeních spravované byl označen klíčovým slovem `__interface`. V nové syntaxi, to je nahrazen `interface class`.

Například následující deklarace třídy ve spravovaných rozšíření:

```
public __gc class Block {};     // reference class
public __value class Vector {}; // value class
public __interface IFooBar {};  // interface class
```

V nové syntaxi tyto jsou ekvivalentně deklarovány následujícím způsobem:

```
public ref class Block {};         // reference class
public value class Vector {};      // value class
public interface class IFooBar {}; // interface class
```

## <a name="specifying-the-class-as-abstract"></a>Určení třídu jako abstraktní

V rámci spravovaného rozšíření, je umístit klíčové slovo `__abstract` před `class` – klíčové slovo (před nebo po `__gc`) k označení, že třída je neúplný a aby objekty třídy nelze vytvořit v rámci programu:

```
public __gc __abstract class Shape {};
public __gc __abstract class Shape2D: public Shape {};
```

V nové syntaxi, zadejte `abstract` kontextové klíčové slovo následující třídy, názvu a před těla třídy, seznam základní třídy nebo středníkem.

```
public ref class Shape abstract {};
public ref class Shape2D abstract : public Shape{};
```

Samozřejmě je sémantický význam beze změny.

## <a name="specifying-the-class-as-sealed"></a>Určení třídy jako zapečetěný

V rámci spravovaného rozšíření, je umístit klíčové slovo `__sealed` před `class` – klíčové slovo (před nebo po `__gc`) k označení, že objekty třídy nelze dědit ze:

```
public __gc __sealed class String {};
```

V nové syntaxi, zadejte `sealed` kontextové klíčové slovo následující třídy, názvu a před těla třídy, seznam základní třídy nebo středníkem.

Můžete jak odvodit třídy a zapečetit. Například `String` třídy je implicitně odvozena z `Object`. Výhodou zapečetění třídy je, že podporuje statické rozlišení (to znamená, že v době kompilace) všech volání virtuální funkce pomocí objektu zapečetěné referenční třídy. Je to proto, `sealed` specifikátor se zaručuje, že `String` sledování popisovače nemůže odkazovat na následně odvozené třídy, které mohou poskytovat instanci přepisující virtuální metody volané. Tady je příklad zapečetěnou třídu v nové syntaxi:

```
public ref class String sealed {};
```

Také můžete specifikovat třídu jako abstraktní a zapečetěná – jedná se o zvláštní, která určuje statické třídě. To je popsán v dokumentaci k modulu CLR následujícím způsobem:

"A typ, který je `abstract` a `sealed` by měl mít jenom statické členy a slouží jako, jak volat některé jazyky oboru názvů."

Tady je příklad, deklarace abstraktní zapečetěné třídy pomocí spravovaných rozšíření syntaxe:

```
public __gc __sealed __abstract class State {
public:
   static State() {}
   static bool inParamList();

private:
   static bool ms_inParam;
};
```

a tady je tato deklarace přeložit na novou syntaxi:

```
public ref class State abstract sealed {
public:
   static State();
   static bool inParamList();

private:
   static bool ms_inParam;
};
```

## <a name="clr-inheritance-specifying-the-base-class"></a>CLR dědičnosti: Určení základní třídy

V rámci modelu objektu CLR je podporován pouze jeden dědění typu public. Spravované rozšíření však zachovává ISO-C++ výchozí výklad základní třídy bez klíčového slova jako zadání privátní odvození. To znamená, že každý CLR zděděná deklarace museli zadat `public` – klíčové slovo chcete přepsat výchozí interpretaci.

```
// Managed Extensions: error: defaults to private derivation
__gc class Derived : Base {};
```

V definici novou syntaxi označuje absenci klíčového slova veřejné odvození v definici CLR dědičnosti. Proto `public` přístup – klíčové slovo je teď volitelné. To sice nevyžaduje žádné úpravy spravovaných rozšíření pro kód jazyka C++, můžu seznamu tuto změnu v tomto poli pro úplnost.

```
// New syntax: ok: defaults to public derivation
ref class Derived : Base{};
```

## <a name="see-also"></a>Viz také

[Spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[abstract](../windows/abstract-cpp-component-extensions.md)<br/>
[sealed](../windows/sealed-cpp-component-extensions.md)