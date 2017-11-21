---
title: "Částečné třídy (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: e4f3b0186d3a7d1aa30ea71f6d80abd5d614e255
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="partial-classes-ccx"></a>Částečné třídy (C + +/ CX)
Částečné třídy je konstruktor, který podporuje scénáře, ve kterých budete upravovat část definice třídy a automatické generování kódu softwaru – například návrháře XAML – je taky úpravy kódu ve stejné třídě. Pomocí konkrétní třídu, můžete zabránit v Návrháři přepsal vašeho kódu. V projektu sady Visual Studio `partial` modifikátor automaticky generovaný soubor.  
  
## <a name="syntax"></a>Syntaxe  
 Chcete-li definovat konkrétní třídu, použijte `partial` – klíčové slovo bezprostředně před klíč třídy z co by se jinak mohly definici běžné třídy. Klíčové slovo jako třeba `partial ref class` je kontextové klíčové slovo, které obsahuje prázdné znaky. V následující konstrukce jsou podporovány částečné definice.  
  
-   `class`nebo`struct`  
  
-   `ref class`nebo`ref struct`  
  
-   `value class`nebo`value struct`  
  
-   `enum`nebo`enum class`  
  
-   `ref interface`, `interface class`, `interface struct`, nebo`__interface`  
  
-   `union`  
  
 Tento příklad ukazuje částečné `ref class`:  
  
 [!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]  
  
## <a name="contents"></a>Obsah  
 Definice částečné třídy může obsahovat všechny položky, které mohou obsahovat definici úplné třídy, pokud `partial` – klíčové slovo byly vynechány. S jednou výjimkou to zahrnuje všechny platná konstrukce, jako jsou základní třídy, datové členy, členské funkce, výčty, friend – deklarace a atributy. A definice vloženého členy statických dat jsou povoleny.  
  
 Jedinou výjimkou je třída usnadnění. Například příkaz `public partial class MyInvalidClass {/* ... */};` chybu. Všechny specifikátory přístupu, které se používají v definici třídu pro MyInvalidClass neovlivňuje výchozí usnadnění v definici následné úplné nebo částečné třídy pro MyInvalidClass.  
  
 Následující fragment kódu ukazuje usnadnění. V první třídu `Method1` je veřejný, protože jeho usnadnění je veřejný. V druhé třídu `Method2` je privátní, protože usnadnění třída výchozí je soukromé.  
  
 [!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]  
  
## <a name="declaration"></a>Deklarace  
 Částečné definice třídy, jako *MyClass* je pouze deklaraci MyClass. To znamená, že by to zavedlo pouze název *MyClass*. *MyClass* nelze použít způsobem, který vyžaduje definice třídy, například zároveň budete vědět, velikost *MyClass* nebo pomocí základní nebo člen *MyClass*. *MyClass* považuje za být definován, pouze když kompilátor narazí definice bez partial *MyClass*.  
  
 Následující příklad ukazuje chování deklarace konkrétní třídu. Po deklaraci #1 *MyClass* lze používat jako v případě, že byly napsány jako dopředného deklarace `ref class MyClass;`. Deklarace #2 je ekvivalentní deklarace #1.Declaration #3 je platný, protože je deklaraci předat dál na třídu. Deklarace #4 je neplatný, ale protože  
  
 *MyClass* není plně definována.  
  
 Deklarace #5 nepoužívá `partial` – klíčové slovo a deklaraci plně definuje *MyClass*. V důsledku toho deklarace #6 je platný.  
  
 [!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]  
  
## <a name="number-and-ordering"></a>Počet a řazení  
 Může být nula nebo více třídu definice pro každý úplné definici třídy.  
  
 Každá třídu definice třídy musí předcházet lexikálně jednu úplnou definici této třídy, ale nemá na atributy stála před dopředného deklarace třídy. Pokud neexistuje úplná definice třídy, pak deklarace třídu lze pouze dopředného deklarace.  
  
 Všechny třídy klíče jako `class` a `struct` se musí shodovat. Například je chyba kódu `partial class X {}; struct X {};`.  
  
 Následující příklad ukazuje počet a řazení. Poslední částečné deklaraci nezdaří, protože třída je již definován.  
  
 [!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]  
  
## <a name="full-definition"></a>Úplná definice  
 V místě úplné definice třídy X chování je stejné jako by měl definici X deklarován všechny základní třídy, členů a tak dále, v pořadí, ve kterém byly došlo a definované v částečné třídy. To znamená, obsah částečné třídy jsou zpracovány jako kdyby byly napsány v místě úplné definice třídy a vyhledání názvu a ostatní jazyk pravidla se použijí v místě úplné definice třídy, jako kdyby obsah částečné třídy napsaných na místě  
  
 Následující příklady kódu dvě mít identické význam a vliv. V prvním příkladu používá konkrétní třídu a v druhém příkladu nepodporuje.  
  
 [!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]  
  
 [!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]  
  
## <a name="templates"></a>Šablony  
 Částečné třídy nelze šablonu.  
  
## <a name="restrictions"></a>Omezení  
 Částečné třídy nemohou pracovat nad rámec jeden překladu jednotky.  
  
 `partial` – Klíčové slovo je podporována pouze v kombinaci s `ref class` – klíčové slovo nebo `value class` – klíčové slovo.  
  
### <a name="examples"></a>Příklady  
 V následujícím příkladu je definován `Address` třída mezi dva soubory kódu. Upraví návrháře `Address.details.h` a změníte `Address.h`. Pouze definice třídy v první soubor se používá `partial` – klíčové slovo.  
  
 [!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]  
  
 [!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)