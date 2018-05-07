---
title: Deklarace spravovaného typu třídy | Microsoft Docs
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
ms.openlocfilehash: 5c821424d8b2669c78befa604bf2669399c89f75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="declaration-of-a-managed-class-type"></a>Deklarace spravovaného typu třídy
Způsob deklarace typu třídy odkazu změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Ve spravovaných rozšíření – třída typu odkazu začíná s `__gc` – klíčové slovo. V nové syntaxe `__gc` – klíčové slovo je nahrazena jednu ze dvou rozložených klíčových slov: `ref class` nebo `ref struct`. Volba `struct` nebo `class` označuje veřejnou (pro `struct`) nebo soukromých (pro `class`) v počáteční neoznačené sekci těla typu deklarována výchozí úroveň přístupu svých členů.  
  
 Podobně je ve spravovaném rozšíření s začíná je hodnota typu třídy `__value` – klíčové slovo. V nové syntaxe `__value` – klíčové slovo je nahrazena jednu ze dvou rozložených klíčových slov: `value class` nebo `value struct`.  
  
 Typ rozhraní v spravovaných rozšíření byl označen klíčovým slovem `__interface`. V nové syntaxe, tím se nahradí `interface class`.  
  
 Například následující třídy deklarace ve spravovaných rozšíření:  
  
```  
public __gc class Block {};     // reference class  
public __value class Vector {}; // value class  
public __interface IFooBar {};  // interface class  
```  
  
 V části nové syntaxe tyto jsou ekvivalentně deklarovány takto:  
  
```  
public ref class Block {};         // reference class  
public value class Vector {};      // value class  
public interface class IFooBar {}; // interface class  
```  
  
## <a name="specifying-the-class-as-abstract"></a>Specifikace jako abstraktní třídy  
 V rámci spravovaných rozšíření umístíte klíčové slovo `__abstract` před `class` – klíčové slovo (buď před nebo po `__gc`) znamená, že třída je nekompletní a aby objekty třídy nelze vytvořit v rámci programu:  
  
```  
public __gc __abstract class Shape {};  
public __gc __abstract class Shape2D: public Shape {};  
```  
  
 V části nové syntaxe, zadejte `abstract` kontextové klíčové slovo následující třídy název a před tělo třídy, seznam odvození základní třídu nebo středníkem.  
  
```  
public ref class Shape abstract {};  
public ref class Shape2D abstract : public Shape{};  
```  
  
 Význam sémantického je samozřejmě beze změny.  
  
## <a name="specifying-the-class-as-sealed"></a>Určující zapouzdřené třídy  
 V rámci spravovaných rozšíření umístíte klíčové slovo `__sealed` před `class` – klíčové slovo (buď před nebo po `__gc`) k označení objekty třídy, které nemůžou být zděděny:  
  
```  
public __gc __sealed class String {};  
```  
  
 V části nové syntaxe, zadejte `sealed` kontextové klíčové slovo následující třídy název a před tělo třídy, seznam odvození základní třídu nebo středníkem.  
  
 Můžete odvození třídy i zapečetit ho. Například `String` implicitně odvozování od `Object`. Výhodou zapečetění třídu je, že podporuje statické řešení (který je při kompilaci) všechna volání virtuální funkce prostřednictvím objektu zapečetěné referenční třídy. Důvodem je, že `sealed` specifikátor zaručuje, že `String` sledovací popisovač nemůže odkazovat na následně odvozené třídy, které mohou poskytovat instanci virtuální metody volané přepsání. Tady je příklad zapečetěné třídy v nové syntaxe:  
  
```  
public ref class String sealed {};  
```  
  
 Také můžete specifikovat třídu jako abstraktní a zapečetěná - Toto je speciální podmínku, která určuje statická třída. To je popsána v dokumentaci CLR takto:  
  
 "A typ, který je `abstract` a `sealed` by měl mít jenom statické členy, a slouží jako, jak volat některé jazyky obor názvů."  
  
 Tady je příklad deklaraci abstraktní zapečetěné třídy pomocí syntaxe spravovaných rozšíření:  
  
```  
public __gc __sealed __abstract class State {  
public:  
   static State() {}  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
 a tady je tuto deklaraci přeložit na nové syntaxe:  
  
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
 V rámci modelu objektu CLR je podporována pouze veřejné jedna dědičnost. Spravovaná rozšíření však zachová výchozí interpretaci ISO C++ bez klíčového slova jako určení soukromého odvození základní třídy. To znamenalo, že každá deklarace dědičnosti CLR měl zajistit `public` – klíčové slovo přepsat výchozí interpretaci.  
  
```  
// Managed Extensions: error: defaults to private derivation  
__gc class Derived : Base {};  
```  
  
 V definici nové syntaxe absence přístupu klíčového slova označuje veřejné odvození v definici dědičnosti CLR. Proto `public` – klíčové slovo přístup je nyní volitelné. To sice nevyžaduje žádné úpravy spravovaných rozšíření pro C++ – kód, I seznam tuto změnu v tomto poli pro úplnost.  
  
```  
// New syntax: ok: defaults to public derivation  
ref class Derived : Base{};  
```  
  
## <a name="see-also"></a>Viz také  
 [Spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)   
 [Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Abstraktní](../windows/abstract-cpp-component-extensions.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)