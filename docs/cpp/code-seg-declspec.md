---
title: code_seg (__declspec) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- code_seg_cpp
dev_langs:
- C++
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6dcf387283aa0d4cdb282760c4ee170a0205172d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068815"
---
# <a name="codeseg-declspec"></a>code_seg (__declspec)

**Specifické pro Microsoft**

**Code_seg** deklarace atributu pojmenuje spustitelný textový segment v souboru .obj, ve kterém bude uložen objektový kód pro funkci nebo funkce člena třídy.

## <a name="syntax"></a>Syntaxe

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>Poznámky

`__declspec(code_seg(...))` Atribut umožňuje umístění kódu do samostatně pojmenovaných segmentů, které lze stránkovat nebo jednotlivě Zamknout v paměti. Tento atribut umožňuje řídit umístění instancí šablon a kódu generovanému kompilátorem.

A *segmentu* je pojmenovaný blok dat v souboru .obj, který je načten do paměti jako celek. A *textový segment* je segment, který obsahuje spustitelný kód. Termín *části* se často zaměňuje s segmentu.

Objektový kód, který je generován, když `declarator` je definována bude umístěn do textového segmentu určené `segname`, což je úzký řetězcový literál. Název `segname` nebude muset zadat [části](../preprocessor/section.md) – Direktiva pragma před použitím v prohlášení. Ve výchozím nastavení, když ne `code_seg` není zadána, objektový kód je umístěn do segmentu nazvaného .text. A **code_seg** atribut přepíše všechny existující [#pragma code_seg](../preprocessor/code-seg.md) směrnice. A **code_seg** atribut použitý na členskou funkci přepíše všechny **code_seg** atribut u nadřazené třídy.

Pokud má entita **code_seg** atribut, všechny deklarace a definice stejné entity musí mít identické **code_seg** atributy. Pokud má základní třídy **code_seg** atribut odvozené třídy musí mít stejný atribut.

Když **code_seg** atributu se použije funkce rozsahu oboru názvů nebo členskou funkci, objektový kód pro tuto funkci je umístěn do zadaného textového segmentu. Pokud je tento atribut aplikován na třídu, všechny členské funkce třídy a vnořené třídy – včetně kompilátorem generované zvláštní členské funkce – jsou umístěny v zadaném segmentu. Místně definované třídy – například třídy definované v hlavní části členské funkce – nedědí **code_seg** atributu nadřazeného rámce.

Když **code_seg** atribut používá šablony třídy nebo funkce šablony, všechny implicitní specializace šablony jsou umístěny v zadané segmentu. Explicitní nebo částečné specializace nedědí **code_seg** atribut z primární šablony. Můžete zadat stejný nebo jiný **code_seg** atribut specializace. A **code_seg** atribut nelze použít explicitní vytváření instancí šablon.

Ve výchozím nastavení je kód generovaný kompilátorem, jako speciální členská funkce, umístěn to segmentu .text. `#pragma code_seg` – Direktiva nemůže přepsat toto výchozí nastavení. Použití **code_seg** atribut na třídu, šablonu třídy nebo šablonu funkce a určete, kde je umístěn kód generovaný kompilátorem.

Výrazy lambda dědí **code_seg** atributy z jejich nadřazených rámců. K určení segmentu pro výraz lambda, použití **code_seg** atribut po klauzuli deklarace parametru a před jakoukoli proměnlivé nebo specifikací výjimky, všechny koncové specifikací návratového typu a hlavní část výrazu lambda. Další informace najdete v tématu [Lambda Expression Syntax](../cpp/lambda-expression-syntax.md). Tento příklad definuje výraz lambda v segmentu s názvem PagedMem:

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Buďte opatrní při uvádění určitých členských funkcí – zejména virtuální členské funkce – do různých segmentů. Pokud definujete virtuální funkci v odvozené třídě, která se nachází ve stránkovaném segmentu, když je metoda základní třídy umístěna v nestránkovaném segmentu, jiné metody základní třídy nebo uživatelský kód mohou předpokládat, že vyvoláním virtuální metody nespustí chybu stránkování.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak **code_seg** atribut ovládá umístění segmentu při implicitní a explicitní specializace šablony se používá:

```cpp
// code_seg.cpp
// Compile: cl /EHsc /W4 code_seg.cpp

// Base template places object code in Segment_1 segment
template<class T>
class __declspec(code_seg("Segment_1")) Example
{
public:
   virtual void VirtualMemberFunction(T /*arg*/) {}
};

// bool specialization places code in default .text segment
template<>
class Example<bool>
{
public:
   virtual void VirtualMemberFunction(bool /*arg*/) {}
};

// int specialization places code in Segment_2 segment
template<>
class __declspec(code_seg("Segment_2")) Example<int>
{
public:
   virtual void VirtualMemberFunction(int /*arg*/) {}
};

// Compiler warns and ignores __declspec(code_seg("Segment_3"))
// in this explicit specialization
__declspec(code_seg("Segment_3")) Example<short>; // C4071

int main()
{
   // implicit double specialization uses base template's
   // __declspec(code_seg("Segment_1")) to place object code
   Example<double> doubleExample{};
   doubleExample.VirtualMemberFunction(3.14L);

   // bool specialization places object code in default .text segment
   Example<bool> boolExample{};
   boolExample.VirtualMemberFunction(true);

   // int specialization uses __declspec(code_seg("Segment_2"))
   // to place object code
   Example<int> intExample{};
   intExample.VirtualMemberFunction(42);
}
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)