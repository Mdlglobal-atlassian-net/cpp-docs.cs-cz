---
title: Přehled generických typů v C++/CLI
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
ms.openlocfilehash: a1a66b6464bf952a530dbf1ea188bfd681d684d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172071"
---
# <a name="overview-of-generics-in-ccli"></a>Přehled generických typů v C++/CLI

Obecné typy jsou parametrizované typy podporované modulem CLR (Common Language Runtime). Parametrizovaný typ je typ, který je definován s neznámým parametrem typu, který je určen při použití obecného.

## <a name="why-generics"></a>Proč obecné typy?

C++podporuje šablony a šablony a obecné typy podporují parametrizované typy pro vytváření typových tříd kolekcí. Šablony však poskytují parametrizace v čase kompilace. Nejde odkazovat na sestavení obsahující definici šablony a vytvořit nové specializace šablony. Po kompilaci bude specializovaná šablona vypadat jako jakákoli jiná třída nebo metoda. Naopak obecné typy jsou vygenerovány v jazyce MSIL jako parametrizovaný typ známý modulem runtime jako parametrizovaný typ; zdrojový kód, který odkazuje na sestavení obsahující obecný typ, může vytvořit specializace obecného typu. Další informace o porovnání standardních C++ šablon a obecných typů naleznete v tématu [generické a šablony (C++/CLI)](generics-and-templates-visual-cpp.md).

## <a name="generic-functions-and-types"></a>Obecné funkce a typy

Typy tříd, pokud jsou spravované typy, mohou být obecné. Příkladem může být `List` třída. Typ objektu v seznamu by byl parametr typu. Pokud jste potřebovali třídu `List` pro mnoho různých typů objektů, před obecnými typy byste mohli použít `List`, který jako typ položky přebírá `System::Object`. To však umožňuje použít v seznamu libovolný objekt (včetně objektů nesprávného typu). Takový seznam by byl označován jako netypové třídy kolekce. Nejlepší je, že můžete typ ověřit za běhu a vyvolat výjimku. Nebo, možná jste použili šablonu, která by po zkompilování do sestavení ztratila obecnou kvalitu. Příjemci sestavení nemohly vytvořit vlastní specializace šablony. Obecné typy umožňují vytvořit typové třídy kolekcí, vyslovit `List<int>` (číst jako "seznam int") a `List<double>` ("seznam dvojitých hodnot"), které by vygenerovaly chybu při kompilaci, pokud jste se pokusili vložit typ, který kolekce není navržena tak, aby přijímala do typové kolekce. Kromě toho tyto typy zůstanou po zkompilování Obecné.

Popis syntaxe obecných tříd může být nalezen v [obecných třídách (C++/CLI)](generic-classes-cpp-cli.md). Nový obor názvů <xref:System.Collections.Generic>zavádí sadu parametrizovaných typů kolekce včetně <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.LinkedList%601>.

Instance a členské funkce, delegáti a globální funkce třídy mohou být také obecné. Obecné funkce mohou být nezbytné v případě, že parametry funkce jsou neznámého typu nebo pokud funkce sama musí fungovat s obecnými typy. V mnoha případech, kde `System::Object` mohl být použit v minulosti jako parametr pro neznámý typ objektu, lze namísto toho použít parametr obecného typu, což umožňuje více kódu bezpečného typu. Jakýkoli pokus o předání typu, pro který funkce nebyla navržena, by byl v době kompilace označen jako chyba. Použití `System::Object` jako parametru funkce, neúmyslné předání objektu, který není určen k tomu, že by se nezjistilo, a je třeba přetypovat neznámý typ objektu na konkrétní typ v těle funkce a účet pro možnost InvalidCastException. S obecným kódem, který se pokouší předat objekt funkci, by způsobil konflikt typu, takže tělo funkce zaručuje správné zadání.

Stejné výhody platí pro třídy kolekcí postavené na obecných typech. Třídy kolekce v minulosti by používaly `System::Object` k ukládání prvků v kolekci. Vložení objektů typu, pro který nebyla kolekce navržena, nebyla v době kompilace označena příznakem, a to často i při vložení objektů. Objekt by se obvykle přetypování na jiný typ při použití v kolekci. Pouze v případě neúspěšného přetypování by byl zjištěn neočekávaný typ. Obecné vyřeší tento problém v době kompilace zjištěním kódu, který vloží typ, který neodpovídá (nebo implicitně převede na) parametr typu Obecné kolekce.

Popis syntaxe najdete v tématu [Obecné funkce (C++/CLI)](generic-functions-cpp-cli.md).

## <a name="terminology-used-with-generics"></a>Terminologie používaná s obecnými typy

### <a name="type-parameters"></a>Parametry typů

Obecná deklarace obsahuje jeden nebo více neznámých typů, které jsou známé jako *parametry typu*. Parametrům typu se předává název, který představuje typ v těle Obecné deklarace. Parametr typu se používá jako typ v těle Obecné deklarace. Obecná deklarace pro `List<T>` obsahuje parametr typu T.

### <a name="type-arguments"></a>Argumenty typu

*Argument typu* je skutečný typ, který se používá namísto parametru typu, když je obecný pro konkrétní typ nebo typy specializované. Například **int** je argument typu v `List<int>`. Typy hodnot a typy popisovačů jsou jediné typy povolené v jako argument obecného typu.

### <a name="constructed-type"></a>Konstruovaný typ

Typ vytvořený z obecného typu je označován jako *konstruovaný typ*. Typ, který není úplně zadaný, jako je například `List<T>`, je *otevřený konstruovaný typ*; typ, který je plný, jako je například `List<double>,`, je *uzavřený konstruovaný typ* nebo *specializovaný typ*. Otevřené konstruované typy mohou být použity v definici jiných obecných typů nebo metod a nesmí být zcela zadány, dokud je nadřazený obecný typ sám určený. Například následující je použití otevřeného konstruovaného typu jako základní třídy pro obecné:

```cpp
// generics_overview.cpp
// compile with: /clr /c
generic <typename T>

ref class List {};

generic <typename T>

ref class Queue : public List<T> {};
```

### <a name="constraint"></a>Jedinečn

Omezení je omezení typů, které lze použít jako parametr typu. Například daná obecná třída může přijmout pouze třídy, které dědí ze zadané třídy nebo implementovat zadané rozhraní. Další informace najdete v tématu [omezení parametrů obecného typuC++(/CLI)](constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="reference-types-and-value-types"></a>Typy odkazů a typy hodnot

Typy a typy hodnot, které mohou být použity jako argumenty typu. V obecné definici, ve kterém lze použít buď typ, je syntaxí odkaz typu odkazu. Například operátor `->` se používá pro přístup ke členům typu parametru typu bez ohledu na to, jestli typ, který se nakonec používá, je odkazový typ nebo typ hodnoty. Když je jako argument typu použit typ hodnoty, modul runtime vygeneruje kód, který používá typy hodnot přímo bez zabalení hodnotových typů.

Při použití typu odkazu jako argumentu obecného typu použijte syntaxi popisovače. Při použití typu hodnoty jako argumentu obecného typu použijte název typu přímo.

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

## <a name="type-parameters"></a>Parametry typů

Parametry typu v obecné třídě se zpracují jako jiné identifikátory. Vzhledem k tomu, že tento typ není znám, existují omezení jejich použití. Například nemůžete použít členy a metody třídy parametrů typu, pokud není parametr typu znám pro podporu těchto členů. To znamená, že pro přístup ke členu prostřednictvím parametru typu je nutné přidat typ, který obsahuje člena do seznamu omezení parametru typu.

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

Tato omezení platí i pro operátory. Neomezený parametr obecného typu nesmí používat operátory `==` a `!=` k porovnání dvou instancí parametru typu pro případ, že typ nepodporuje tyto operátory. Tyto kontroly jsou nezbytné pro obecné typy, ale ne pro šablony, protože obecné typy mohou být specializované za běhu s jakoukoliv třídou, která splňuje omezení, pokud je příliš pozdě pro kontrolu použití neplatných členů.

Výchozí instanci parametru typu lze vytvořit pomocí operátoru `()`. Příklad:

`T t = T();`

kde `T` je parametr typu v obecné třídě nebo definici metody, inicializuje proměnnou na výchozí hodnotu. Pokud `T` je ref class, bude ukazatel s hodnotou null; Pokud `T` je hodnotovou třídou, je objekt inicializován na hodnotu nula. Nazývá se *výchozí inicializátor*.

## <a name="see-also"></a>Viz také

[Obecné typy](generics-cpp-component-extensions.md)
