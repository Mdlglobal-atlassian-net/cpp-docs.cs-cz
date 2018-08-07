---
title: Reprezentace plovoucí desetinné čárky IEEE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61545d57a8a42f45616bd788defacaba12785971
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608238"
---
# <a name="ieee-floating-point-representation"></a>Reprezentace plovoucí desetinné čárky IEEE

Microsoft Visual C++ je konzistentní s číselnou standardů IEEE. Standard IEEE 754 popisuje s plovoucí desetinnou čárkou formátů, způsob, jak reprezentaci reálná čísla v hardwaru. Existují aspoň pět interní formát pro čísla s plovoucí desetinnou čárkou, která jsou reprezentovat hardwaru cílem a kompilátorem MSVC, ale kompilátor používá pouze dva z nich. *Jednoduchou přesností* (4bajtová) a *dvojité přesnosti* formáty (8 bajtů) se používají v jazyce Visual C++. Jednoduchou přesnost je deklarována pomocí klíčového slova **float**. Dvojitá přesnost je deklarována pomocí klíčového slova **double**. IEEE standard také určuje *precision polovině* (2bajtových) a *čtyřikrát přesností* formáty (16 bajtů), ale i *dvojité rozšířené přesnosti* (10 bajtů) formát, který některé kompilátory jazyků C a C++ implementovat jako **long double** datového typu. V kompilátoru jazyka Visual C++ **long double** datový typ je považován za odlišný typ, ale typ úložiště mapuje na **double**. Existuje, ale vnitřní a sestavení jazykovou podporu pro výpočty pomocí dalších formátů, včetně dvojité rozšířené přesnosti (10 bajtů) formát, kde je podporovaný hardware.

Hodnoty jsou uloženy následujícím způsobem:

|Hodnota|Uložené jako|
|-----------|---------------|
|jednoduchou přesností|podepsat bit, 8 bitů exponent, 23 bitů mantisy|
|dvojité přesnosti|podepsat bit, 11bitový exponent, mantisy 52-bit|
|dvojité rozšířené přesnosti|podepsat bit, 15-bit exponent, 64-bit mantisy|

Ve formátech, jednoduchou a dvojitou přesností, je předpokládané přední 1 v zlomkové části, volá se *mantisy* (a někdy označovány jako *mantisa*), která je nebyly uloženy v paměti, takže significandy jsou ve skutečnosti 24 nebo 53 bitů, i když jsou uloženy pouze 23 nebo 52 bitů. Formát dvojité rozšířené přesnosti ve skutečnosti ukládá tento bit.

Polovinu své možné hodnoty jsou tendenční exponenty. To znamená, že se že od sebe odečítáte Tento posun z uložené exponent, chcete-li získat skutečný exponent. Pokud uložené exponent je menší než posun, je ve skutečnosti záporného exponentu.

Exponenty jsou tendenční následujícím způsobem:

|Exponent|Tendenční podle|
|--------------|---------------|
|8 bitů (jednoduchou přesností)|127|
|verze 11 (dvojité přesnosti)|1023|
|15-bit (dvojité extended přesnosti)|16383|

Tyto exponenty nejsou mocnin desíti; jsou to mocniny dvou. To znamená uložené exponenty 8 bitů v rozsahu-127 až 127 uložené jako 0 až 254. Hodnota 2<sup>127</sup> zhruba odpovídá 10<sup>38</sup>, což je skutečná limit jednoduchou přesností.

Mantisa se ukládá jako zlomek binární formuláře 1.XXX.... Tato část obsahuje hodnotu větší než nebo rovno 1 a menší než 2. Všimněte si, že reálná čísla byly vždy uloženy ve *normalized formuláře*; to znamená, mantisy je posunuta doleva o tak, aby nejvyšším bit mantisa je vždy 1. Protože je tento bit je vždy 1, předpokládá se (není uložené) ve formátu jednoduchou a dvojitou přesností. (Není desítkové) řádová je považován za právě napravo od předních 1.

Formát, pak pro různé velikosti je následujícím způsobem:

|Formát|1 bajt|Bajtů 2|Bajtů 3|Bajtů 4|...|n bajtů|
|------------|------------|------------|------------|------------|---------|------------|
|jednoduchou přesností| `SXXXXXXX`|`XMMMMMMM`|`MMMMMMMM`|`MMMMMMMM`|||
|dvojité přesnosti|`SXXXXXXX`|`XXXXMMMM`|`MMMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|
|dvojité rozšířené přesnosti|`SXXXXXXX`|`XXXXXXXX`|`1MMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|

`S` představuje bit znaménka `X`společnosti posunutého exponentu bitů a `M`společnosti jsou mantisy bitů. Všimněte si, že se předpokládá, že ve formátech, jednoduchou a dvojitou přesností nejvíce vlevo bit, ale je k dispozici jako "1" v bajtu 3 na rozšířené – formát s dvojitou přesností.

Chcete-li posunout binární bodu správně, nejprve unbias exponent a přejdete binární bodu vpravo nebo left odpovídající počet bitů.

## <a name="special-values"></a>Speciální hodnoty

S plovoucí desetinnou čárkou formáty jsou některé hodnoty, které jsou speciálně zpracovány.

### <a name="zero"></a>Nula

Nula nelze normalizovat, takže se dají přičtení ve formuláři normalizované hodnoty jednoduchou a dvojitou přesností. Představuje speciální bitový vzor všemi nulovými hodnotami 0. Je také možné představující - 0 jako nula znaménkem nastaven bit, ale - 0 a 0 vždycky porovnání rovnají.

### <a name="infinities"></a>Nekonečno

+ ∞ a −∞ hodnoty jsou reprezentovány exponent samých jedniček a mantisy všemi nulovými hodnotami. Kladné a záporné nekonečno lze znázornit pomocí bit znaménka.

### <a name="subnormals"></a>Subnormals

Je možné k vyjádření čísla velikost menší než nejmenší normalizované číslo. Tato čísla jsou označovány jako *subnormal* nebo *denormal* čísla. Je-li exponent se všemi nulovými hodnotami a říká mantisa je nenulová, implicitní přední bit mantisy považuje rovno nule, není jednou. Přesnost čísel subnormal ocitne mimo provoz, protože počet počáteční nuly ve mantisy přejde.

### <a name="nan---not-a-number"></a>NaN – nejedná se o číslo

Je možné k reprezentaci hodnoty, které nejsou reálné číslo, například 0 / 0, ve formátu s plovoucí desetinnou čárkou IEEE. Hodnota tohoto druhu se nazývá *NaN*. NaN je reprezentován exponent samých jedniček a mantisy nenulové. Existují dva druhy hodnoty NaN, *quiet* hodnoty NaN, nebo QNaNs, a *signalizaci* hodnoty NaN, nebo SNaNs. Hodnoty tichý NaN mít počáteční objektem v mantisy a obecně nerozšíří prostřednictvím výrazu. Představují neurčitá hodnota, jako je například výsledkem dělení nekonečno nebo součinu nekonečno nulou. Zabezpečovací hodnoty NaN mít počáteční nuly v mantisy. Ty se používají pro operace, které nejsou platné, který signalizuje, že s plovoucí desetinnou čárkou hardwarové výjimky.

## <a name="examples"></a>Příklady

Toto jsou některé příklady ve formátu jednoduchou přesnost:

- Pro hodnotu 2 je bit znaménka 0 a uložené exponent je 128 nebo 1000 0000 v binárním souboru, který je 127 plus 1. Uložené binární mantisa je (1). 000 0000 0000 0000 0000 0000, která má implicitní přední 1 a binární bod, takže skutečný mantisy představuje jedno.

   |Hodnota|Vzorec|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |2|1 * 2<sup>1</sup>|0100 0000 0000 0000 0000 0000 0000 0000|0x40000000|

- Hodnota -2. Stejné jako + 2 s tím rozdílem, že je nastavena na bit znaménka. To platí pro záporné hodnoty všech čísel s plovoucí desetinnou čárkou IEEE formátu.

   |Hodnota|Vzorec|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |-2|-1 * 2<sup>1</sup>|1100 0000 0000 0000 0000 0000 0000 0000|0xC0000000|

- Hodnota 4. Stejné mantisy exponent zvýší o 1 (posunutého hodnotu 129, nebo 100 0000 1 v binárním souboru.

   |Hodnota|Vzorec|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |4|1 * 2<sup>2</sup>|0100 0000 1000 0000 0000 0000 0000 0000|0x40800000|

- Hodnotu 6. Stejné exponent mantisy je větší polovinu – jeho (1). 100 0000 ... 0000 0000, který, protože se jedná binární zlomek je 1. 1/2, protože hodnoty zlomkové číslice 1/2, 1/4, 1/8 a tak dále.

   |Hodnota|Vzorec|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |6|1.5 * 2<sup>2</sup>|0000 0100 1100 0000 0000 0000 0000 0000|0x40C00000|

- Hodnota 1. Stejné mantisy jako ostatní mocniny dvou posunutého exponent je jeden méně než dvě 127 nebo 011 1111 1 v binárním souboru.

   |Hodnota|Vzorec|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |1|1 * 2<sup>0</sup>|0011 1111 1000 0000 0000 0000 0000 0000|0x3F800000|

- Hodnota 0,75. Posunutého exponent je 126 011 1111 0 v binárním souboru a říká mantisa je (1). 100 0000 ... 0000 0000, což je 1. 1/2.

   |Hodnota|Vzorec|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |0.75|1.5 * 2<sup>-1</sup>|0011 1111 0100 0000 0000 0000 0000 0000|0x3F400000|

- Hodnota 2.5. Stejně jako dvě kromě toho, že je bit, který představuje 1/4 je nastavena v mantisy.

   |Hodnota|Vzorec|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |2.5|1,25 * 2<sup>1</sup>|0100 0000 0010 0000 0000 0000 0000 0000|0x40200000|

- 1/10 je opakovaný zlomek v binárním souboru. Mantisa je právě tvy 1.6, a posunutého exponent říká, že má být děleno 16 1.6 (je 1 1101 011 v binárním souboru, který je 123 v desítkové soustavě). True exponent je 123-127 = - 4, což znamená, že faktor, podle kterého se má vynásobit 2<sup>-4</sup> = 1/16. Všimněte si, že uložené mantisy se zaokrouhluje nahoru v poslední verzi, pokus o přičtení číslo představující co nejpřesněji. (Z důvodu 1/10 do 1/100 se nemusí přesně reprezentovat v binárním souboru se podobá z důvodu, že se nemusí přesně reprezentovat v desítkové soustavě 1/3.)

   |Hodnota|Vzorec|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |0.1|1.6 * 2<sup>-4</sup>|0011 1101 1100 1100 1100 1100 1100 1101|0x3DCCCCCD|

- Nula je zvláštní případ, který používá tento vzorec pro minimální možné reprezentovatelné kladné hodnoty, které obsahuje samé nuly.

   |Hodnota|Vzorec|Binární reprezentace|Šestnáctková hodnota|
   |-|-|-|-|
   |0|1 * 2<sup>-128</sup>|0000 0000 0000 0000 0000 0000 0000 0000|0x00000000|

## <a name="see-also"></a>Viz také:

[Proč čísla s plovoucí desetinnou čárkou můžou ztratit přesnost](../../build/reference/why-floating-point-numbers-may-lose-precision.md)