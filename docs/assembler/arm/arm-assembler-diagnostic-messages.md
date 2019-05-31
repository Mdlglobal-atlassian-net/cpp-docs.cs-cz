---
title: Diagnostické zprávy assembleru ARM
ms.date: 08/30/2018
f1_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
helpviewer_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
ms.openlocfilehash: 72c1ea64501ef8104fee9bdf914a1464c07c3b76
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449223"
---
# <a name="arm-assembler-diagnostic-messages"></a>Diagnostické zprávy assembleru ARM

Assembler Microsoft ARM (*armasm*) vysílá diagnostických upozornění a chyby, pokud se setká s nimi. Tento článek popisuje zprávy nejvíce došlo.

## <a name="syntax"></a>Syntaxe

> <em>Název souboru</em> **(** <em>číslo řádku</em> **):** \[ **chyba**|**upozornění** ] **A**<em>číslo</em> **:** *zprávy*

## <a name="diagnostic-messages---errors"></a>Diagnostické zprávy – chyby

> A2193: generuje tento pokyn nepředvídatelné chování.

Architektura ARM nemůže zaručit, co se stane při spuštění této instrukce.  Podrobné informace o jasně definované formy tento pokyn, [ARM architektuře referenčním manuálu](https://go.microsoft.com/fwlink/p/?linkid=246464).

```asm
    ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior
```

> A2196: instrukce nemůže být kódovaný v 16 bitů

Zadaná instrukce nemůže být kódovaný jako instrukcí Thumb 16 bitů.  Zadejte pokyn 32-bit nebo změna uspořádání kódem, aby cílový popisek do rozsahu 16bitových instrukce.

Assembler můžou snažit kódování větve v 16 bitů a neúspěšné a zobrazí se tato chyba, i když je 32-bit pobočkové kódovat. Tento problém můžete vyřešit použitím `.W` specifikátor explicitně označit větev jako 32-bit.

```asm
    ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits

    B.W label             ; OK
    B.N label             ; A2196: instruction cannot be encoded in 16 bits
    SPACE 10000
label
```

> A2202: Syntaxe příkazu Pre-protokolování přístupu uživatele není povoleno v oblasti JEZDCE

Kód pro Thumb nutné použít syntaxi Unified jazyka assembleru (UAL).  Stará syntaxe už je přijat.

```asm
    ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region
    ADDSEQ r0, r1         ; OK
```

> A2513: Otočení musí být sudá

V režimu ARM je alternativní syntaxe pro určení konstanty.  Místo psaní `#<const>`, můžete napsat `#<byte>,#<rot>`, která představuje konstantní hodnota, která se získá hodnota otáčení `<byte>` právo `<rot>`.  Při použití této syntaxe je třeba hodnotu `<rot>` i.

```asm
    MOV r0, #4, #2       ; OK
    MOV r0, #4, #1       ; A2513: Rotation must be even
```

> A2557: Nesprávný počet bajtů ke zpětnému zápisu

Struktury NEON načítají a ukládají pokyny (`VLDn`, `VSTn`), existuje alternativní syntaxe pro určení zpětného zápisu do základní registrace.  Namísto vložení hodnoty vykřičník (!) za adresou, můžete zadat okamžitou hodnotu, která označuje posun být přidán do základní registrace.  Pokud použijete tuto syntaxi, musíte zadat přesný počet bajtů, které byly načteny nebo neukládá podle pokynů.

```asm
    VLD1.8 {d0-d3}, [r0]!         ; OK
    VLD1.8 {d0-d3}, [r0], #32     ; OK
    VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back
```

## <a name="diagnostic-messages---warnings"></a>Diagnostické zprávy – upozornění

> A4228: Hodnota zarovnání větší než zarovnání oblasti; není zaručeno, že zarovnání

Zarovnání ve stanoveném `ALIGN` direktiva je větší než zarovnání nadřazený `AREA`.  V důsledku toho, assembler nemůže zaručit, že `ALIGN` – direktiva se neuplatňují.

To pokud chcete napravit, můžete zadat na `AREA` – direktiva `ALIGN` atribut, který je roven nebo větší než požadované zarovnání.

```asm
AREA |.myarea1|
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed

AREA |.myarea2|,ALIGN=3
ALIGN 8           ; OK
```

> A4508: Použití této otočený konstanty je zastaralé

V režimu ARM je alternativní syntaxe pro určení konstanty.  Místo psaní `#<const>`, můžete napsat `#<byte>,#<rot>`, která představuje konstantní hodnota, která se získá hodnota otáčení `<byte>` právo `<rot>`.  V některých kontextech ARM přestala používat tyto otočený konstant. V těchto případech použijte základní `#<const>` syntaxe místo.

```asm
    ANDS r0, r0, #1                ; OK
    ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated
```

> A4509: Tato forma podmíněné instrukce je zastaralý.

Tato forma podmíněné instrukce je zastaralá ve ARM v architektuře ARMv8. Doporučujeme vám, že změníte kód, který použije podmínkových větví. Pokud chcete zobrazit, které podmíněné pokyny jsou stále podporovány, naleznete [ARM architektuře referenčním manuálu](https://go.microsoft.com/fwlink/p/?linkid=246464).

Toto upozornění není, protože když ho **- oldit** použít přepínač příkazového řádku.

```asm
    ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated
```

## <a name="see-also"></a>Viz také:

[Referenční dokumentace pro použití nástroje assembleru ARM v příkazovém řádku](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Direktivy assembleru ARM](../../assembler/arm/arm-assembler-directives.md)<br/>
