---
title: Přehled obecných typů v jazyce C + +/ CLI
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], about generics
- default initializers [C++]
- type parameters [C++]
- constructed types
- type arguments [C++]
- constructed types, open [C++]
- open constructed types [C++]
- constructed types, closed [C++]
ms.assetid: 21f10637-0fce-4916-b925-6c86a126d3aa
ms.openlocfilehash: 1105025ebebdfcbce723505747f6677674c04334
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655166"
---
# <a name="overview-of-generics-in-ccli"></a>Přehled obecných typů v jazyce C + +/ CLI

Obecné typy jsou parametrizované typy podporované modulem common language runtime. Parametrizované typ je typ, který je definován s parametrem Neznámý typ, který je zadán, pokud se používá Obecné.

## <a name="why-generics"></a>Proč obecných typů?

Jazyk C++ podporuje šablony a obě šablony a obecné typy podporují parametrizované typy pro vytvoření typu kolekce tříd. Nicméně šablony poskytují Parametrizace za kompilace. Nemůže odkazovat na sestavení obsahující definice šablony a vytvořte nový specializace šablony. Po kompilaci, specializovaná šablona vypadá jiné třídy nebo metody. Naproti tomu jsou emitovány obecné typy v jazyce MSIL jako parametry typu ví, modul runtime typ s parametry; zdrojový kód, který odkazuje na sestavení obsahující obecný typ, můžete vytvořit specializace obecného typu. Další informace o porovnání standardní šablony jazyka C++ a obecnými typy najdete v tématu [obecné typy a šablony (C + +/ CLI)](../windows/generics-and-templates-visual-cpp.md).

## <a name="generic-functions-and-types"></a>Obecné funkce a typy

Typy tříd, jako jsou spravované typy, může být obecné. Příkladem může být `List` třídy. Typ objektu v seznamu by parametr typu. V případě potřeby můžete `List` třídy pro mnoho různých typů objektů, než jste možná použili obecné typy `List` , která přebírá `System::Object` jako typu položky. Ale pro použití v seznamu, který by umožnilo libovolného objektu (včetně objektů nesprávného typu). Tento seznam by byla volána bez typu kolekce třídy. Nejlépe může kontrola typu za běhu a vyvolají výjimku. Nebo jste možná použili, šablonu, která by dojít ke ztrátě jeho obecné kvality po kompilaci do sestavení. Uživatelé vašeho sestavení nebylo možné vytvořit vlastní specializace šablony. Obecné typy umožňují vytvářet třídy typu kolekce, Dejme tomu, že `List<int>` (Číst jako "Seznam int") a `List<double>` ("seznam pečlivě") který vygeneruje Chyba kompilace, pokud jste se pokusili umístit typ, který byl v kolekci není nastaven na přijímání do zadaného objektu kolekce. Kromě toho zůstat tyto typy Obecné, když jsou zkompilovány.

Popis syntaxe obecné třídy lze nalézt v [obecné třídy (C + +/ CLI)](../windows/generic-classes-cpp-cli.md). Nový obor názvů, <xref:System.Collections.Generic>, představuje sadu parametrizovaných kolekci typů včetně <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.LinkedList%601>.

Jak instance a členské funkce statických tříd, delegátů a globální funkce může také být obecné. Obecné funkce může být nutné, pokud jsou parametry funkce neznámého typu, nebo pokud samotné funkce musí pracovat s obecných typů. V mnoha případech, kdy `System::Object` pravděpodobně byl použit v minulosti jako parametr pro neznámý objekt typu, parametr obecného typu může místo toho použít umožňující další kód zajišťující bezpečnost typů. Jakékoli pokusy o předat typ, který funkci nebyl navržen pro by označených jako chyba v době kompilace. Pomocí `System::Object` jako parametr funkce, zvyšuje ochranu před nechtěnými předání objektu by zjistil, že funkce není určen k řešení, a je třeba přetypovat Neznámý typ objektu na určitý typ v těle funkce a pro účet možnost k InvalidCastException. S obecnou kód pokus o předání objektu funkce způsobí konflikt typu, je zaručeno, že tělo funkce správného typu.

Stejné výhody platí pro třídy kolekce založená na obecné typy. Třídy kolekcí v minulosti by použít `System::Object` na ukládání prvků v kolekci. Vložení objekty tohoto typu kolekce nebyl navržen pro nebyl označen jako v době kompilace a často není i v případě, že objekty byly vloženy. Objekt by obvykle přetypovat na jiný typ, když se použila v kolekci. Pouze v případě, že se nezdařilo přetypování by neočekávaný typ zjistit. Obecné typy řeší tento problém v době kompilace nalezením veškerý kód, který vloží typ, který neodpovídá (nebo implicitně převést na) parametr typu obecné kolekce.

Popis syntaxe, naleznete v tématu [obecné funkce (C + +/ CLI)](../windows/generic-functions-cpp-cli.md).

## <a name="terminology-used-with-generics"></a>Terminologie použitá s obecnými typy

### <a name="type-parameters"></a>Parametry typu

Obecná deklarace obsahuje jednu nebo více neznámé typy, které jsou známé jako *parametry typu*. Název, což je zkratka pro typ v těle obecná deklarace jsou uvedeny parametry typu. Parametr typu se používá jako typ v těle obecná deklarace. Obecná deklarace pro `List<T>` obsahuje parametr typu T.

### <a name="type-arguments"></a>Argumenty typu

*Argument typu* je skutečný typ zastoupen parametr typu, když Obecné se specializuje na určitý typ nebo typy. Například **int** je argument typu v `List<int>`. Typy hodnot a popisovače typy jsou pouze typy v povolené jako argument obecného typu.

### <a name="constructed-type"></a>Konstruovaný typ.

Typ vytvořený z obecného typu se označuje jako *konstruovaný typ*. Zadaný typ není plně, jako například `List<T>` je *otevřete konstruovaný typ*; typ plně zadaný, jako například `List<double>,` je *uzavřený konstruovaný typ* nebo *specializovaný typ* . Otevřené sestavené typy lze použít v definici další obecné typy a metody a nesmí se zadávat plně, dokud uzavírající Obecné je sama o sobě zadat. Následující je příklad, použití otevřít konstruovaný typ jako základní třída pro obecný:

```cpp
// generics_overview.cpp
// compile with: /clr /c
generic <typename T>

ref class List {};

generic <typename T>

ref class Queue : public List<T> {};
```

### <a name="constraint"></a>Omezení

Omezení je omezení na typy, které může sloužit jako parametr typu. Například dané obecnou třídu může přijímat pouze třídy, které dědí z dané třídy nebo implementovat zadané rozhraní. Další informace najdete v tématu [omezení parametrů obecných typů (C + +/ CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="reference-types-and-value-types"></a>Typy odkazů a hodnotových typech

Popisovače typů a typů hodnot může použít jako argumenty typu. V obecné definici, ve kterém může být používán, syntaxe je to, že odkazových typů. Například `->` operátor se používá pro přístup ke členům typu parametru typu, zda je typ nakonec použít odkazový typ nebo hodnotový typ. Když typ hodnoty se používá jako argument typu, modul runtime generuje kód, který používá typy hodnot přímo bez zabalení typů hodnot.

Při použití typu odkaz jako argument obecného typu, použijte syntaxi popisovač. Při použití typu hodnoty jako argument obecného typu, použijte název typu přímo.

```cpp
// generics_overview_2.cpp
// compile with: /clr
generic <typename T>

ref class GenericType {};
ref class ReferenceType {};

value struct ValueType {};

int main() {
    GenericType<ReferenceType^> x;
    GenericType<ValueType> y;
}
```

## <a name="type-parameters"></a>Parametry typu

Parametry typu v obecné třídě zachází stejně jako jiné identifikátory. Ale vzhledem k tomu, typ kroku není znám, existují omezení pro jejich použití. Nelze například použít členy a metody parametru typu třídy, pokud parametr typu se označuje pro podporu těchto členů. To znamená, že pro přístup ke členu prostřednictvím parametru typu, je nutné přidat typ, který obsahuje člena do seznamu omezení parametru typu.

```cpp
// generics_overview_3.cpp
// compile with: /clr
interface class I {
   void f1();
   void f2();
};

ref struct R : public I {
   virtual void f1() {}
   virtual void f2() {}
   virtual void f3() {}
};

generic <typename T>
where T : I
void f(T t) {
   t->f1();
   t->f2();
   safe_cast<R^>(t)->f3();
}

int main() {
   f(gcnew R());
}
```

Tato omezení platí pro operátory také. Nelze použít jako parametr obecného typu bez omezení `==` a `!=` operátoři k porovnání dvou instancí parametru typu, v případě, typ nepodporuje tyto operátory. Tyto kontroly jsou nezbytné pro obecné typy, ale ne pro šablony, protože obecných typů může být specializovaná za běhu s libovolnou třídu, která splňuje omezení, pokud je již příliš pozdě ke kontrole použijte neplatní členové.

Výchozí instance parametru typu mohou být vytvořeny pomocí `()` operátor. Příklad:

`T t = T();`

kde `T` je parametr typu v definici třídy nebo metody obecného, inicializuje proměnnou na výchozí hodnotu. Pokud `T` je třída ref je ukazatel s hodnotou null; Pokud `T` hodnotová třída je objekt je inicializován na hodnotu nula. Jedná se *výchozí inicializátor*.

## <a name="see-also"></a>Viz také

[Obecné typy](../windows/generics-cpp-component-extensions.md)