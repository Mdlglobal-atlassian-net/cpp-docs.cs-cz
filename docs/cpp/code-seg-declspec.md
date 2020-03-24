---
title: code_seg (__declspec)
ms.date: 11/04/2016
f1_keywords:
- code_seg_cpp
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
ms.openlocfilehash: 22703e92b1a127378c965ce12bcc4e5475b3e452
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180833"
---
# <a name="code_seg-__declspec"></a>code_seg (__declspec)

**Specifické pro společnost Microsoft**

Atribut deklarace **code_seg** pojmenovává spustitelný textový segment v souboru. obj, ve kterém budou uloženy kód objektu pro funkci nebo členské funkce třídy.

## <a name="syntax"></a>Syntaxe

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>Poznámky

Atribut `__declspec(code_seg(...))` umožňuje umístění kódu do samostatných pojmenovaných segmentů, které mohou být stránkované nebo uzamčené v paměti jednotlivě. Tento atribut umožňuje řídit umístění instancí šablon a kódu generovanému kompilátorem.

*Segment* je pojmenovaný blok dat v souboru. obj, který je načten do paměti jako jednotka. *Textový segment* je segment, který obsahuje spustitelný kód. *Oddíl* Term se často používá k zaměnitelné segmenty.

Kód objektu, který je generován při definování `declarator` je vložen do textového segmentu určeného `segname`, což je úzký řetězcový literál. Název `segname` nemusí být zadán v [oddílu](../preprocessor/section.md) pragma, aby jej bylo možné použít v deklaraci. Ve výchozím nastavení, pokud není zadána žádná `code_seg`, je kód objektu umístěn do segmentu s názvem. text. Atribut **code_seg** přepisuje všechny existující direktivy [#pragma code_seg](../preprocessor/code-seg.md) . Atribut **code_seg** aplikovaný na členskou funkci přepíše všechny atributy **code_seg** použité pro ohraničující třídu.

Pokud má entita atribut **code_seg** , musí mít všechny deklarace a definice stejné entity stejné **code_seg** atributy. Pokud má základní třída atribut **code_seg** , odvozené třídy musí mít stejný atribut.

Pokud je atribut **code_seg** použit pro funkci oboru oboru názvů nebo členskou funkci, je kód objektu pro tuto funkci vložen do zadaného textového segmentu. Pokud je tento atribut aplikován na třídu, všechny členské funkce třídy a vnořené třídy – včetně kompilátorem generované zvláštní členské funkce – jsou umístěny v zadaném segmentu. Lokálně definované třídy – například třídy definované v těle členské funkce – nedědí atribut **code_seg** ohraničujícího oboru.

Když je atribut **code_seg** použit pro třídu šablony nebo funkci šablony, jsou všechny implicitní specializace šablony vloženy do zadaného segmentu. Explicitní nebo Částečná specializace nedědí atribut **code_seg** z primární šablony. U specializace můžete zadat stejný nebo jiný atribut **code_seg** . Atribut **code_seg** nelze použít pro explicitní vytváření instancí šablony.

Ve výchozím nastavení je kód generovaný kompilátorem, jako speciální členská funkce, umístěn to segmentu .text. Direktiva `#pragma code_seg` nepřepisuje tuto výchozí hodnotu. Použijte atribut **code_seg** pro třídu, šablonu třídy nebo šablonu funkce k určení, kde je kód generovaný kompilátorem vložen.

Výrazy lambda dědí **code_seg** atributy z jejich ohraničujícího rozsahu. Chcete-li určit segment pro lambda, použijte atribut **code_seg** za klauzulí deklarace parametru a před jakoukoli proměnlivou specifikací nebo specifikací výjimek, jakoukoli specifikací návratového typu a tělo výrazu lambda. Další informace naleznete v tématu [syntaxe výrazu lambda](../cpp/lambda-expression-syntax.md). Tento příklad definuje výraz lambda v segmentu s názvem PagedMem:

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Buďte opatrní při uvádění určitých členských funkcí – zejména virtuální členské funkce – do různých segmentů. Pokud definujete virtuální funkci v odvozené třídě, která se nachází ve stránkovaném segmentu, když je metoda základní třídy umístěna v nestránkovaném segmentu, jiné metody základní třídy nebo uživatelský kód mohou předpokládat, že vyvoláním virtuální metody nespustí chybu stránkování.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak atribut **code_seg** řídí umístění segmentu, pokud je použita implicitní specializace šablony:

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
