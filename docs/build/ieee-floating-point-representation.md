---
title: Reprezentace plovoucí desetinné čárky IEEE
ms.date: 05/06/2019
helpviewer_keywords:
- float keyword
- real*8 value
- floating-point numbers, IEEE representation
- double data type, floating-point representation
- IEEE floating point representation
- real*10 value
- long double
- real*4 value
ms.assetid: 537833e8-fe05-49fc-8169-55fd0314b195
ms.openlocfilehash: de132dcf28747cd866229cff8972e2aed271a047
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630358"
---
# <a name="ieee-floating-point-representation"></a>Reprezentace plovoucí desetinné čárky IEEE

Microsoft C++ (MSVC) je konzistentní s numerickými standardy standardu IEEE. Standard IEEE-754 popisuje formáty s plovoucí desetinnou čárkou, způsob reprezentace reálných čísel v hardwaru. Existuje alespoň pět interních formátů pro čísla s plovoucí desetinnou čárkou, která jsou reprezentována v hardwaru cíleném kompilátorem MSVC, ale kompilátor používá pouze dva z nich. Formáty s *jednou přesností* (4 bajty) a *dvojitou přesností* (8 bajtů) se používají v MSVC. Jednoduchá přesnost je deklarována pomocí klíčového slova **float**. Dvojitá přesnost je deklarována pomocí klíčového slova **Double**. Standard IEEE také určuje formáty s *poloviční přesností* (2 bajty) a *čtyřnásobné* (16 bajtů), jakož i formát s dvojitou přesností (10 bajt), který některé C a C++ kompilátory implementují jako typ **Long.** datový typ Double. V kompilátoru MSVC je datový typ **Long Double** považován za odlišný typ, ale typ úložiště je mapován na hodnotu **Double**. Nicméně podpora vnitřních a sestavových aplikací pro výpočty používá jiné formáty, včetně formátu Double-Extended-Precision (10 bajtů), pokud to hardware podporuje.

Hodnoty jsou uloženy následujícím způsobem:

|Value|Uloženo jako|
|-----------|---------------|
|jednoduchá přesnost|bit znaménka, 8bitový exponent, 23 bitů mantisa|
|Dvojitá přesnost|bit znaménka, 11 exponent, 52-bit mantisa|
|Dvojitá rozšířená přesnost|bit znaménka, 15 bitů exponent, 64-bit mantisa|

Ve formátech s jednoduchou přesností a dvojitou přesností se předpokládá první 1 část zlomku, která se nazývá *mantisa* (a někdy se označuje jako mantisa), která není uložená v paměti, takže hodnot jsou ve skutečnosti 24 nebo 53. bity, i když jsou uložené jenom 23 nebo 52 bitů. Formát s dvojitou přesností ve skutečnosti ukládá tento bit.

Exponenty jsou posunuty o polovinu možné hodnoty. To znamená, že odečtete tento posun od uloženého exponentu a získáte skutečný exponent. Pokud je uložený exponent menší než posun, je ve skutečnosti záporné exponent.

Exponenty jsou posunuty následujícím způsobem:

|Zmocněn|Posunuto od|
|--------------|---------------|
|8 bitů (s jednoduchou přesností)|127|
|11 bitů (dvojitá přesnost)|1023|
|15 bitů (dvojitá rozšířená přesnost)|16383|

Tyto exponenty nepatří do deseti. jsou to dvě mocniny. To znamená, že 8bitové uložené exponenty mohou být v rozsahu od-127 do 127 a uloženy jako 0 až 254. Hodnota 2<sup>127</sup> je přibližně rovna 10<sup>38</sup>, což je skutečný limit s jednoduchou přesností.

Mantisa je uložen jako binární zlomek formuláře 1.XXX.... Hodnota tohoto zlomku je větší nebo rovna 1 a menší než 2. Všimněte si, že reálné hodnoty jsou vždy uloženy v *normalizované podobě*; To znamená, že mantisa je ponechán posunutý tak, že horní bit mantisa je vždy 1. Vzhledem k tomu, že tento bit je vždy 1, předpokládá se (neuložený) ve formátech s jednoduchou přesností a dvojitou přesností. Předpokládá se, že binární (ne desítkový) bod je jenom napravo od první 1.

Formát pro různé velikosti je následující:

|Formát|bajt 1|bajt 2|bajt 3|bajt 4|...|bajt n|
|------------|------------|------------|------------|------------|---------|------------|
|jednoduchá přesnost| `SXXXXXXX`|`XMMMMMMM`|`MMMMMMMM`|`MMMMMMMM`|||
|Dvojitá přesnost|`SXXXXXXX`|`XXXXMMMM`|`MMMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|
|Dvojitá rozšířená přesnost|`SXXXXXXX`|`XXXXXXXX`|`1MMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|

`S`představuje bit znaménka, `X`jsou posunutými exponenty `M`a jsou mantisa bity. Všimněte si, že bit nejvíce vlevo se předpokládá ve formátech s jednoduchou přesností a dvojitou přesností, ale je přítomný jako "1" v bajtu 3 ve formátu dvojité rozšířené přesnosti.

Chcete-li binární bod správně posunout, nejprve odsuňte exponent a pak jeho binární bod napravo doprava nebo doleva o příslušný počet bitů.

## <a name="special-values"></a>Speciální hodnoty

Formáty s plovoucí desetinnou čárkou obsahují některé hodnoty, které jsou speciálně ošetřeny.

### <a name="zero"></a>Nula

Hodnotu nula nelze normalizovat, což znamená, že je nereprezentace v normalizované podobě hodnoty s jednoduchou přesností nebo dvojitou přesností. Speciální Bitová maska všech nul představuje 0. Je také možné vyjádřit hodnotu-0 jako nulu s nastaveným bitem znaménka, ale-0 a 0 vždy porovnat jako EQUAL.

### <a name="infinities"></a>Nekonečno

Hodnoty + ∞ a − ∞ představují exponent všech a mantisa všech nul. Kladné i záporné nekonečno lze znázornit pomocí bitu znaménka.

### <a name="subnormals"></a>Normály

Je možné vyjádřit čísla menší velikosti než nejmenší normalizované číslo. Tato čísla se označují jako *normální* nebo *deobvyklá* čísla. Pokud je exponent vše nula a mantisa je nenulový, pak implicitní počáteční bit mantisa je považován za nulu, nikoli na jeden. Přesnost meziběžných čísel se zapíná jako počet počátečních nul v mantisa.

### <a name="nan---not-a-number"></a>NaN – nejedná se o číslo.

Je možné znázornit hodnoty, které nejsou reálné číslo, například 0/0, ve formátu IEEE s plovoucí desetinnou čárkou. Hodnota tohoto druhu se nazývá *NaN*. NaN je reprezentovaná exponentem všech a nenulovým mantisa. Existují dva druhy hodnoty NaN, *quiet* hodnoty NaN, QNaNs a signalizace hodnoty NaN nebo SNaNs. Tiché hodnoty NaN mít v mantisa první, a obecně se šíří prostřednictvím výrazu. Představují neurčitou hodnotu, například výsledek dělení podle nekonečna nebo vynásobení nekonečna nulou. signalizace hodnoty NaN má v mantisa počáteční nulu. Používají se pro operace, které nejsou platné, k signalizaci hardwarové výjimky s plovoucí desetinnou čárkou.

## <a name="examples"></a>Příklady

Níže jsou uvedeny některé příklady ve formátu s jednou přesností:

- Pro hodnotu 2 je bit znaménka nula a uložený exponent je 128 nebo 1000 0000 v binárním souboru, což je 127 plus 1. Uložený binární mantisa je (1.) 000 0000 0000 0000 0000 0000, který má implicitní úvodní 1 a binární bod, takže skutečný mantisa je jeden.

   |Value|Receptuře|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |2|1 * 2<sup>1</sup>|0100 0000 0000 0000 0000 0000 0000 0000|0x40000000|

- Hodnota – 2. Stejné jako + 2 s tím rozdílem, že je bit znaménka nastaven. To platí pro záporné číslo s plovoucí desetinnou čárkou ve formátu IEEE.

   |Value|Receptuře|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |-2|-1 * 2<sup>1</sup>|1100 0000 0000 0000 0000 0000 0000 0000|0xC0000000|

- Hodnota 4. Stejné mantisa, exponent se zvyšuje o jednu (hodnota s posunutím je 129 nebo 100 0000 1 v binárním souboru.

   |Value|Receptuře|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |4|1 * 2<sup>2</sup>|0100 0000 1000 0000 0000 0000 0000 0000|0x40800000|

- Hodnota 6. Stejné exponenty, mantisa je větší po polovině – je (1.) 100 0000 ... 0000 0000, což znamená, že se jedná o binární zlomek, který je 1 1/2, protože hodnoty zlomkových číslic jsou 1/2, 1/4, 1/8 a tak dále.

   |Value|Receptuře|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |6|1,5 * 2<sup>2</sup>|0100 0000 1100 0000 0000 0000 0000 0000|0x40C00000|

- Hodnota 1. Stejné mantisa jako jiné mocniny dvou, je nejnižším exponentem jedna méně než dvě v 127 nebo 011 1111 1 v binárním souboru.

   |Value|Receptuře|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |1|1 * 2<sup>0</sup>|0011 1111 1000 0000 0000 0000 0000 0000|0x3F800000|

- Hodnota 0,75. Posunutý exponent je 126, 011 1111 0 v binárním souboru a mantisa je (1.) 100 0000 ... 0000 0000, což je 1 1/2.

   |Value|Receptuře|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |0.75|1,5 * 2<sup>– 1</sup>|0011 1111 0100 0000 0000 0000 0000 0000|0x3F400000|

- Hodnota 2,5. Přesně stejný jako u dvou s tím rozdílem, že bit, který představuje 1/4, je nastaven v mantisa.

   |Value|Receptuře|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |2.5|1,25 * 2<sup>1</sup>|0100 0000 0010 0000 0000 0000 0000 0000|0x40200000|

- 1/10 je opakující se zlomky v binárním formátu. Mantisa je pouze nesmělí abyste 1,6 a posunutý exponent říká, že 1,6 má být děleno 16 (v binárním souboru je 011 1101 1, což je 123 v desítkovém formátu). Skutečný exponent je 123-127 =-4, což znamená, že faktor, kterým se má vynásobit, je 2<sup>– 4</sup> = 1/16. Všimněte si, že uložené mantisa se zaokrouhlují nahoru v posledním bitu – pokus vyjádřit co nejblížeelné číslo co nejpřesněji. (Důvod 1/10 a 1/100 není přesně reprezentovatelné v binárním souboru je podobný důvodu, že 1/3 není přesně reprezentovatelné v desítkové soustavě.)

   |Value|Receptuře|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |0.1|1,6 * 2<sup>– 4</sup>|0011 1101 1100 1100 1100 1100 1100 1101|0x3DCCCCCD|

- Nula je zvláštní případ, který používá vzorec pro minimální možnou reprezentovatelné kladné hodnoty, což je nula.

   |Value|Receptuře|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |0|1 * 2<sup>-128</sup>|0000 0000 0000 0000 0000 0000 0000 0000|0x00000000|

## <a name="see-also"></a>Viz také:

[Proč čísla s plovoucí desetinnou čárkou můžou ztratit přesnost](why-floating-point-numbers-may-lose-precision.md)