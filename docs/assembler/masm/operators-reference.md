---
title: Referenční dokumentace k operátorům MASM | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c9f5beb0e3525de6df88e44248410810502962e
ms.sourcegitcommit: 4cbde5d164d681204c4011dc95a921d75292f423
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49459150"
---
# <a name="masm-operators-reference"></a>Referenční dokumentace k operátorům MASM

## <a name="arithmetic"></a>Aritmetické operace

||||
|-|-|-|
|[* (vynásobit)](operator-multiply.md)|[+ (Přidat)](operator-add.md)|[-(odečíst nebo negovat)](operator-subtract-2.md)|
|[. (pole)](operator-dot.md)|[/ (dělení)](operator-subtract-1.md)|[&#91;&#93;(index)](operator-brackets.md)|
|[MOD (zbytek)](operator-mod.md)|||

## <a name="control-flow"></a>Tok řízení

||||
|-|-|-|
|[\! (prostředí runtime logický operátor not)](operator-logical-not-masm-run-time.md)|[\!= (nerovná runtime)](operator-not-equal-masm.md)|[&#124;&#124;(logický modul runtime nebo)](operator-logical-or.md)|
|[& & (logický modul runtime a)](operator-logical-and-masm-run-time.md)|[< (prostředí runtime menší než)](operator-less-than-masm-run-time.md)|[\<= (prostředí runtime menší nebo rovno)](operator-less-or-equal-masm-run-time.md)|
|[== (prostředí runtime rovno)](operator-equal-masm-run-time.md)|[> (větší než runtime)](operator-greater-than-masm-run-time.md)|[> = (prostředí runtime větší nebo rovno)](operator-greater-or-equal-masm-run-time.md)|
|[& (bitový modulu runtime a)](operator-bitwise-and.md)|||
|[CARRY? (runtime carry test)](operator-carry-q.md)|[OVERFLOW? (test přetečení runtime)](operator-overflow-q.md)|[PARITY? (runtime parity test)](operator-parity-q.md)|
|[SIGN? (test přihlašování runtime)](operator-sign-q.md)|[NULA? (prostředí runtime nula test)](operator-zero-q.md)||

## <a name="logical-and-shift"></a>Logické a Shift

||||
|-|-|-|
|[A (bitový a)](operator-and.md)|[Ne (bitový operátor not)](operator-not.md)|[OR (bitový nebo)](operator-or.md)|
|[Shl – (shift bits vlevo)](operator-shl.md)|[Shr – (shift bits vpravo)](operator-shr.md)|[XOR (bitový exkluzivní nebo)](operator-xor.md)|

## <a name="macro"></a>– Makro

||||
|-|-|-|
|[\! (znakový literál)](operator-logical-not-masm.md)|[% (nakládání jako text)](operator-percent.md)||
|[;; (považovat komentář)](operator-semicolons.md)|[&lt; &gt; (považovat za jeden literál)](operator-literal.md)|[& & (Nahraďte hodnotu parametru)](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>Různé

||||
|-|-|-|
|["" (zpracovávat jako řetězec)](operator-single-quote.md)|["" (zpracovávat jako řetězec)](operator-double-quote.md)||
|: (místní Popisek definice)|:: (registrovat segmentu a posunu)|:: (globální Popisek definice)|
|[; (považovat komentář)](operator-semicolon.md)|[DUP (při opakovaném deklarace)](operator-dup.md)||

## <a name="record"></a>Záznam

|||
|-|-|
|[MASKA (získat záznam nebo pole bitová maska)](operator-mask.md)|[Šířka (získat šířku záznam nebo pole)](operator-width.md)|

## <a name="relational"></a>Relační

||||
|-|-|-|
|[EQ (rovná)](operator-eq.md)|[GE (větší nebo rovno)](operator-ge.md)|[GT (větší než)](operator-gt.md)|
|[LE (menší nebo rovno)](operator-le.md)|[LT (menší než)](operator-lt.md)|[NE (není rovno)](operator-ne.md)|

## <a name="segment"></a>Segment

|||
|-|-|
|[: (segmentovat přepsání)](operator-colon.md)|:: (registrovat segmentu a posunu)|
|[IMAGEREL (image relativním posunem)](operator-imagerel.md)|[LROFFSET (zavaděč přeložit posunu)](operator-lroffset.md)|
|[POSUN (relativním posunem segmentu)](operator-offset.md)|[SECTIONREL (relativním posunem část)](operator-sectionrel.md)|
|[SEG (get segmentu)](operator-seg.md)||

## <a name="type"></a>Typ

||||
|-|-|-|
|[Vysoká (8 bitů nejnižší 16 bitů)](operator-high.md)|[HIGH32 (32 bitů 64 bitů)](operator-high32.md)|[HIGHWORD (16 bitů nejnižší 32 bitů)](operator-highword.md)|
|[Délka (počet prvků v poli)](operator-length.md)|[LENGTHOF (počet prvků v poli)](operator-lengthof.md)|[Nízká (8 bitech)](operator-low.md)|
|[LOW32 (nedostatek 32 bitů)](operator-low32.md)|[LOWWORD (nízké 16 bitů)](operator-lowword.md)|[OPATTR (informace o typu argumentu get)](operator-opattr.md)|
|[PTR (ukazatel na nebo jako typ)](operator-ptr.md)|[SHORT (krátký popis značky)](operator-short.md)|[VELIKOST (velikost typu nebo proměnné)](operator-size.md)|
|[SIZEOF (velikost typu nebo proměnné)](operator-sizeof.md)|[Toto (aktuální umístění)](operator-this.md)|[Typ (typ výrazu get)](operator-type.md)|
|[. Typ (informace o typu argumentu get)](operator-dot-type.md)|||

## <a name="see-also"></a>Viz také:

[Microsoft Macro Assembler – referenční dokumentace](microsoft-macro-assembler-reference.md)<br/>
