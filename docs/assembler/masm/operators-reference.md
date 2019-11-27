---
title: Reference k operátorům MASM
ms.date: 08/30/2018
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: 5295307ad668b76e5ff39882ce2613f2042f914a
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74395215"
---
# <a name="masm-operators-reference"></a>Reference k operátorům MASM

## <a name="arithmetic"></a>Aritmetické operace

||||
|-|-|-|
|[* (násobení)](operator-multiply.md)|[+ (Přidat)](operator-add.md)|[– (odečíst nebo negace)](operator-subtract-2.md)|
|[. dílčí](operator-dot.md)|[/(rozdělit)](operator-subtract-1.md)|[&#91;&#93;indexovacím](operator-brackets.md)|
|[MOD (zbytek)](operator-mod.md)|||

## <a name="control-flow"></a>Tok řízení

||||
|-|-|-|
|[\! (logická modul runtime)](operator-logical-not-masm-run-time.md)|[\!= (modul runtime se nerovná)](operator-not-equal-masm.md)|[&#124;&#124;(modul runtime nebo logický)](operator-logical-or.md)|
|[& & (logická prostředí a)](operator-logical-and-masm-run-time.md)|[< (běhové prostředí je menší než)](operator-less-than-masm-run-time.md)|[\<= (běhové prostředí je menší nebo rovno)](operator-less-or-equal-masm-run-time.md)|
|[= = (runtime EQUAL)](operator-equal-masm-run-time.md)|[> (modul runtime je větší než)](operator-greater-than-masm-run-time.md)|[> = (runtime je větší nebo rovno)](operator-greater-or-equal-masm-run-time.md)|
|[& (modul runtime bitových a)](operator-bitwise-and.md)|||
|[ÚMYSL? (běh se testem)](operator-carry-q.md)|[PLNĚ? (test přetečení modulu runtime)](operator-overflow-q.md)|[Parita? (test parity za běhu)](operator-parity-q.md)|
|[OSOBĚ? (běhový test podpisu)](operator-sign-q.md)|[VYNULUJTE? (běhový test s hodnotou nula)](operator-zero-q.md)||

## <a name="logical-and-shift"></a>Logický operátor and Shift

||||
|-|-|-|
|[AND (bitové a)](operator-and.md)|[NOT (bitový not)](operator-not.md)|[NEBO (bitový operátor OR)](operator-or.md)|
|[SHL – (posun Shift vlevo)](operator-shl.md)|[SHR – (Shift bity vpravo)](operator-shr.md)|[XOR (bitový exkluzivní operátor OR)](operator-xor.md)|

## <a name="macro"></a>– Makro

||||
|-|-|-|
|[\! (znakový literál)](operator-logical-not-masm.md)|[% (považovat za text)](operator-percent.md)||
|[;; (považován za komentář)](operator-semicolons.md)|[&lt; &gt; (považovat za jeden literál)](operator-literal.md)|[& & (náhradní hodnota parametru)](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>Různé

||||
|-|-|-|
|[' ' (považován za řetězec)](operator-single-quote.md)|["" (považovat za řetězec)](operator-double-quote.md)||
|: (definice místní jmenovky)|:: (registrovat segment a posunutí)|:: (definice globálního popisku)|
|[; (považován za komentář)](operator-semicolon.md)|[DUP (opakování deklarace)](operator-dup.md)||

## <a name="record"></a>Záznam

|||
|-|-|
|[MASKA (získání maskování dat nebo pole)](operator-mask.md)|[Šířka (získání záznamu nebo šířky pole)](operator-width.md)|

## <a name="relational"></a>Relační

||||
|-|-|-|
|[EQ (rovná se)](operator-eq.md)|[GE (větší nebo rovno)](operator-ge.md)|[GT (je větší než)](operator-gt.md)|
|[LE (menší nebo rovno)](operator-le.md)|[LT (je menší než)](operator-lt.md)|[NE (není rovno)](operator-ne.md)|

## <a name="segment"></a>Letu

|||
|-|-|
|[: (přepsání segmentu)](operator-colon.md)|:: (registrovat segment a posunutí)|
|[IMAGEREL (relativní posunutí obrázku)](operator-imagerel.md)|[LROFFSET (posun přeložený zavaděčem)](operator-lroffset.md)|
|[POSUN (relativní Posun segmentu)](operator-offset.md)|[SECTIONREL – (relativní posun oddílu)](operator-sectionrel.md)|
|[SEG – (načíst segment)](operator-seg.md)||

## <a name="type"></a>Typ

||||
|-|-|-|
|[Vysoká (horních 8 bitů s nejnižší hodnotou 16 bitů)](operator-high.md)|[HIGH32 – (vysoké 32 bitů 64 bitů)](operator-high32.md)|[HIGHWORD (vysoké 16 bitů s nejnižší 32 bity)](operator-highword.md)|
|[Délka (počet prvků v poli)](operator-length.md)|[LENGTHOF (počet prvků v poli)](operator-lengthof.md)|[NÍZKÁ (nízká, 8 bitů)](operator-low.md)|
|[LOW32 – (nízké 32 bity)](operator-low32.md)|[LOWWORD (nízká úroveň 16 bitů)](operator-lowword.md)|[OPATTR (získání informací o typu argumentu)](operator-opattr.md)|
|[PTR (ukazatel na nebo jako typ)](operator-ptr.md)|[SHORT (označit krátký typ popisku)](operator-short.md)|[VELIKOST (velikost typu nebo proměnné)](operator-size.md)|
|[SIZEOF (velikost typu nebo proměnné)](operator-sizeof.md)|[Toto (aktuální umístění)](operator-this.md)|[TYP (získat typ výrazu)](operator-type.md)|
|[. TYP (získat informace o typu argumentu)](operator-dot-type.md)|||

## <a name="see-also"></a>Viz také:

[Microsoft Macro Assembler – referenční dokumentace](microsoft-macro-assembler-reference.md)<br/>
