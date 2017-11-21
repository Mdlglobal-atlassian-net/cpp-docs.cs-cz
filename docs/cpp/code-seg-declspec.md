---
title: code_seg (__declspec) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: code_seg_cpp
dev_langs: C++
helpviewer_keywords: code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f1e222e3fb78807f4c67c746677e1223c7776a41
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="codeseg-declspec"></a>code_seg (__declspec)
**Konkrétní Microsoft**  
  
 `code_seg` Názvy atributů deklarace segment spustitelné textu v souboru .obj, ve kterém se uloží objekt kódu pro funkce nebo funkce člena třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec(code_seg("segname")) declarator  
```  
  
## <a name="remarks"></a>Poznámky  
 `__declspec(code_seg(...))` Atribut umožňuje umístění kódu na samostatné s názvem segmentů, které můžete stránkovaného nebo uzamčena v paměti jednotlivě. Tento atribut umožňuje řídit umístění instancí šablon a kódu generovanému kompilátorem.  
  
 A *segment* je pojmenované blok dat v souboru .obj, který je načten do paměti jako jednotku. A *text segmentu* je segment, který obsahuje spustitelný kód. Termín *části* se často používá zcela zaměnitelným významem segmentu.  
  
 Objekt kódu, která vygenerovala při `declarator` je definována uveden text segmentu určeného `segname`, což je úzké řetězcový literál. Název `segname` nemusí být zadán v [části](../preprocessor/section.md) – Direktiva pragma před použitím v deklaraci. Ve výchozím nastavení, pokud žádné `code_seg` je zadán kód objekt je umístěn segment s názvem text. A `code_seg` atribut přepíše všechny existující [#pragma code_seg](../preprocessor/code-seg.md) – direktiva. A `code_seg` atribut použitý členské funkce přepsání žádné `code_seg` atribut nadřazených třídy použít.  
  
 Pokud má entita `code_seg` atribut, všechny deklarace a definice stejné entity, musí mít identické `code_seg` atributy. Pokud má základní třídy `code_seg` atribut odvozené třídy musí mít stejný atribut.  
  
 Když `code_seg` je použit atribut funkce oboru názvů nebo členské funkce, kód objektu pro tuto funkci je umístěn v segmentu zadaný text. Pokud je tento atribut aplikován na třídu, všechny členské funkce třídy a vnořené třídy – včetně kompilátorem generované zvláštní členské funkce – jsou umístěny v zadaném segmentu. Místně definované třídy – například tříd definovaných v těle funkce na člen – nedědí `code_seg` atribut vymezeném oboru.  
  
 Když `code_seg` atribut se používá ke třídě šablony nebo šablony funkce, všechny implicitní specializací šablony jsou umístěny do zadaného segmentu. Explicitní nebo jeho část specializací nedědí `code_seg` atribut z primární šablony. Můžete určit stejné nebo jiné `code_seg` atribut specializace. A `code_seg` atributu nelze použít vytvoření instance explicitní šablony.  
  
 Ve výchozím nastavení je kód generovaný kompilátorem, jako speciální členská funkce, umístěn to segmentu .text. `#pragma code_seg` – Direktiva nemůže přepsat toto výchozí nastavení. Použití `code_seg` atribut na třídu, šablona třídy nebo funkce šablony k řízení, kde generované kompilátorem kód je umístěn.  
  
 Lambdas dědění `code_seg` atributů z jejich vymezeném oboru. Chcete-li určit segment pro lambda, použít `code_seg` atribut po klauzuli deklarace parametru a před spuštěním měnitelný nebo specifikace výjimek, všechny koncové specifikace návratový typ a text lambda. Další informace najdete v tématu [syntaxe výrazu Lambda](../cpp/lambda-expression-syntax.md). Tento příklad definuje výraz lambda v segmentu s názvem PagedMem:  
  
```cpp  
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };  
```  
  
 Buďte opatrní při uvádění určitých členských funkcí – zejména virtuální členské funkce – do různých segmentů. Pokud definujete virtuální funkci v odvozené třídě, která se nachází ve stránkovaném segmentu, když je metoda základní třídy umístěna v nestránkovaném segmentu, jiné metody základní třídy nebo uživatelský kód mohou předpokládat, že vyvoláním virtuální metody nespustí chybu stránkování.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak `code_seg` ovládací prvky atribut segmentovat umístění při implicitní a explicitní šablony specializace se používá:  
  
```  
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
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)