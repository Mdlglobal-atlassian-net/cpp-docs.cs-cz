---
title: "Přehled obecných typů v jazyce Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
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
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6699d446fadbc0ca380bea28df318c27a31c04e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="overview-of-generics-in-visual-c"></a>Přehled obecných typů ve Visual C++
Obecné typy jsou parametrizované typy podporované systémem modul common language runtime. Parametrizované typ je typ, který je definován s parametrem neznámého typu, která je zadána při Obecné se používá.  
  
## <a name="why-generics"></a>Proč obecné?  
 C++ nepodporuje šablony a oba a obecné typy podporují parametrizované typy pro vytvoření třídy typu kolekce. Šablony ale poskytují Parametrizace kompilaci. Nelze odkazovat na sestavení, která obsahuje definice šablony a vytvořit nové specializací šablony. Jakmile zkompilován, šablonu specializované vypadá jako ostatní třída nebo metoda. Naproti tomu jsou vygenerované obecné typy v MSIL jako parametrizované typ ví modulem runtime typu parametrizované; zdrojový kód, který odkazuje na sestavení obsahující obecného typu můžete vytvořit specializací obecného typu. Další informace o porovnání šablony Visual C++ a obecnými typy najdete v tématu [obecné typy a šablony (Visual C++)](../windows/generics-and-templates-visual-cpp.md).  
  
## <a name="generic-functions-and-types"></a>Obecné funkce a typy  
 Typy tříd, dokud jsou spravované typy, může být obecný. Příkladem může být `List` třídy. Typ objektu v seznamu by být parametr typu. Můžete podle potřeby `List` třídu pro mnoho různých typů objektů, než byste použili obecné typy `List` , která má **System::Object** jako typ položky. Ale které by se použít v seznamu umožňují libovolného objektu (včetně objektů nesprávného typu). Tento seznam bude volat třídu bez typu kolekce. Může v nejlépe kontrola typu za běhu a způsobí výjimku. Nebo použili jste šablonu, která by dojít ke ztrátě jeho obecné kvality jednou zkompilovány do sestavení. Příjemci ve vašem sestavení nebylo možné vytvořit vlastní specializací šablony. Obecné typy umožňují například vytvoření třídy typu kolekce, `List<int>` (přečíst jako "Seznam int") a `List<double>` ("seznam dvojitou") Pokud jste se pokusili typ, který byl kolekce, které by generují chyby kompilace není nastaven na přijímání do zadaného objektu kolekce. Kromě toho tyto typy zůstanou obecné po, že se kompilují.  
  
 Popis syntaxe obecné třídy lze nalézt v [obecné třídy (C + +/ CLI)](../windows/generic-classes-cpp-cli.md) `.` nový obor názvů, <xref:System.Collections.Generic>, představuje sadu parametrizované kolekci typů, včetně <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Generic.List%601>a <xref:System.Collections.Generic.LinkedList%601>.  
  
 Jak instance a statická třída členské funkce, delegáti a globální funkce mohou být také obecné. Obecné funkce může být nutné, pokud funkce parametry jsou neznámého typu, nebo pokud samotnou funkci, musíte spolupracovat s obecné typy. V mnoha případech kde **System::Object** pravděpodobně byl použit v minulosti jako parametr pro typ objektu Neznámý parametr obecného typu může místo toho použít povolení pro další kód bezpečnost typů. Pokusy o předat typ, který funkce nebyla určená pro bude označena jako chyba v době kompilace. Pomocí **System::Object** jako parametr funkce nechtěnému předávání objektu, funkce nebyla určená k řešení nerozpoznaly, a budete muset přetypovat Neznámý typ objektu na konkrétní typ aplikace tělo funkce a účet s možností k InvalidCastException. S obecný kód pokouší předat objekt funkce by způsobilo konflikt typu tak tělo funkce záruku, že se tak, aby měl správného typu.  
  
 Stejné výhody se vztahují na třídy kolekce založená na obecné typy. Třídy kolekce v minulosti využije **System::Object** k uložení elementů v kolekci. Vkládání objekty typu, který kolekce nebyl navržený pro nebyl příznakem v době kompilace a často není i v případě, že byly vloženy objekty. Objekt by obvykle přetypovat na jiný typ, když přistupoval v kolekci. Pouze v případě, že se nezdařilo přetypování by neočekávaný typ zjistit. Obecné typy řeší tento problém v době kompilace tím zjišťování kód, který se vloží typ, který není shodují (nebo implicitně převést na) parametr typu obecné kolekce.  
  
 Popis syntaxi najdete v tématu [obecné funkce (C + +/ CLI)](../windows/generic-functions-cpp-cli.md).  
  
## <a name="terminology-used-with-generics"></a>Terminologie použitá s obecnými typy  
  
##### <a name="type-parameters"></a>Parametry typu  
 Obecné deklarace obsahuje minimálně jeden neznámý typ označuje jako *parametry typu*. Parametry typu mají název, který zastupuje typu v textu obecné deklarace. Parametr typu se používá jako typ v textu obecné deklarace. Obecné deklaraci pro seznam < T\> obsahuje parametr typu T.  
  
##### <a name="type-arguments"></a>Argumenty typů  
 *Argument typu* je skutečný typ používají místo parametr typu, pokud se specializuje obecné pro konkrétní typ nebo typy. Například `int` je argument typu v `List<int>`. Typy hodnot a popisovač typy jsou pouze typy, které jsou povoleny v jako argument obecného typu.  
  
##### <a name="constructed-type"></a>Vytvořený typ  
 Typ vytvářejí na základě obecného typu se označuje jako *sestavený typu*. Zadaný typ není plně, jako například `List<T>` je *otevřete vytvořený typ*; plně zadaný, například typ `List<double>,` je *uzavřený vytvořený typ* nebo *specializuje typu* . Otevřené sestavené typy mohou být použity v definici jiné obecné typy nebo metody a nesmí být zadán plně, dokud uzavření obecné je sám zadán. Následující příklad se používá otevřené sestavené typu jako základní třída pro obecný:  
  
 `// generics_overview.cpp`  
  
 `// compile with: /clr /c`  
  
 `generic <typename T>`  
  
 `ref class List {};`  
  
 `generic <typename T>`  
  
 `ref class Queue : public List<T> {};`  
  
##### <a name="constraint"></a>Omezení  
 Omezení je omezení na typy, které mohou být použity jako parametr typu. Například dané obecná třída může přijímat pouze třídy, které dědí od zadané třídy, nebo jsou implementovány specifikované rozhraní. Další informace najdete v tématu [omezení obecných parametrů typů (C + +/ CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## <a name="reference-types-and-value-types"></a>Odkazové typy a typy hodnot  
 Obslužné rutiny a hodnotové typy slouží jako argumenty typu. V definici obecné, ve kterém mohou být použity buď typ, syntaxe je u odkazové typy. Například  **->**  operátor se používá pro přístup k členům typ parametru typu, zda je typ nakonec používá odkazového typu nebo typ hodnoty. Pokud je jako argument typu použit typ hodnoty, modul runtime generuje kód, který používá typy hodnot přímo bez zabalení typů hodnot.  
  
 Při použití typu odkazu. jako argument obecného typu, použijte syntaxi popisovač. Pokud používáte typ hodnoty jako argument obecného typu, použijte název typu přímo.  
  
 `// generics_overview_2.cpp`  
  
 `// compile with: /clr`  
  
 `generic <typename T>`  
  
 `ref class GenericType {};`  
  
 `ref class ReferenceType {};`  
  
 `value struct ValueType {};`  
  
 `int main() {`  
  
 `GenericType<ReferenceType^> x;`  
  
 `GenericType<ValueType> y;`  
  
 `}`  
  
## <a name="type-parameters"></a>Parametry typu  
 Parametry typu v obecné třídy jsou zpracovány jako další identifikátory. Ale protože typ není znám, existují omezení pro jejich použití. Nelze například použít členy a metody třídy parametr, pokud parametr typu je známé pro podporu těchto členů. To znamená o přístup člena prostřednictvím typ parametru, musíte přidat typ, který obsahuje člena do seznamu omezení parametr typu.  
  
 `// generics_overview_3.cpp`  
  
 `// compile with: /clr`  
  
```  
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
  
 Tato omezení platí pro operátory také. Nesmíte používat bez omezení obecného typu parametru `==` a `!=` operátory k porovnání dvou instancí parametru typu, v případě, že typ nepodporuje tyto operátory. Tyto kontroly jsou nezbytné pro obecné typy, ale není pro šablony, protože Obecné může specializuje za běhu pomocí všechny třídy, splňuje omezení, pokud je příliš pozdě Zkontrolujte použití neplatní členové.  
  
 Výchozí instanci parametr typu je možné vytvářet pomocí `()` operátor. Příklad:  
  
 `T t = T();`  
  
 kde `T` je parametr typu v definici obecná třída nebo metoda, inicializuje proměnnou na výchozí hodnotu. Pokud `T` je třída ref bude ukazatel s hodnotou null; Pokud `T` třídou, která hodnota je objekt inicializován na hodnotu nula. Tento postup se nazývá *výchozí inicializátoru*.  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy](../windows/generics-cpp-component-extensions.md)