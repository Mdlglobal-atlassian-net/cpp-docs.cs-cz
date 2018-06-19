---
title: Diagnostické zprávy assembleru ARM | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1616b4bd9c4b64e771ec537a1b8cd7b582702222
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052770"
---
# <a name="arm-assembler-diagnostic-messages"></a>Diagnostické zprávy assembleru ARM
Assembleru Microsoft ARM (*armasm*) zjistí, je-li vysílá diagnostiky upozornění a chyby. Tento článek popisuje zprávy nejvíce došlo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
filename(lineno) : [error|warning] Anum: message  
```  
  
## <a name="diagnostic-messages"></a>Diagnostické zprávy  
  
### <a name="errors"></a>Chyby  
 A2193: Tento pokyn generuje nepředvídatelné chování  
 Architektura ARM nemůže zaručit, co se stane, když se spustí tento pokyn.  Podrobné informace o dobře definovaný formy tento pokyn [ARM architektura referenční příručce](http://go.microsoft.com/fwlink/p/?linkid=246464).  
  
```  
  
ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior  
  
```  
  
 A2196: instrukce nemůže být kódovaný jako 16 bitů  
 Zadaný pokyn nelze kódovaný jako instrukci jezdec 16 bitů.  Zadejte instrukce 32-bit nebo změna uspořádání kód pro zajištění popisek cílový rozsah 16bitové instrukcí.  
  
 Assembleru můžou snažit kódování větve v 16 bitů a neúspěšné a zobrazí se tato chyba, i když je 32-bit větev kódovat. Tento problém můžete vyřešit pomocí `.W` specifikátor explicitně označit větev jako 32bitová verze.  
  
```  
  
  ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits  
  
  B.W label             ; OK  
  B.N label             ; A2196: instruction cannot be encoded in 16 bits  
  SPACE 10000  
label  
  
```  
  
 A2202: Syntaxe příkazu Pre-UAL není povoleno v oblasti JEZDEC  
 Kód jezdec musí pomocí syntaxe jazyka Unified assembleru (UAL).  Staré syntaxe již byla přijata.  
  
```  
  
ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region  
ADDSEQ r0, r1         ; OK  
  
```  
  
 A2513: Otočení musí být sudá.  
 V režimu ARM je alternativní syntaxe pro určení konstanty.  Místo psaní `#<const>`, můžete napsat `#<byte>,#<rot>`, která představuje konstantní hodnota, která se získala při otáčení hodnota `<byte>` přímo pomocí `<rot>`.  Při použití této syntaxe je třeba hodnotu `<rot>` i.  
  
```  
  
MOV r0, #4, #2       ; OK  
MOV r0, #4, #1       ; A2513: Rotation must be even  
  
```  
  
 A2557: Nesprávný počet bajtů ke zpětnému zápisu  
 Ve struktuře NEÓNOVÁ spouštění a ukládání pokyny (`VLDn`, `VSTn`), dojde alternativní syntaxe pro určení zpětného zápisu na základní registrace.  Namísto po adresu uvedení vykřičníkem (!), můžete zadat okamžité hodnotu, která určuje posun být přidán do základní registrace.  Pokud chcete použít tuto syntaxi, musíte zadat přesné počet bajtů, které byly nebo uložené podle pokynů.  
  
```  
  
VLD1.8 {d0-d3}, [r0]!         ; OK  
VLD1.8 {d0-d3}, [r0], #32     ; OK  
VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back  
  
```  
  
### <a name="warnings"></a>Upozornění  
 A4228: Zarovnání hodnota přesahuje zarovnání oblasti; zarovnání není zaručena.  
 Zarovnání, který je uveden v `ALIGN` – direktiva je větší než zarovnání uzavření `AREA`.  V důsledku toho, assembleru nemůže zaručit, že `ALIGN` – direktiva bude použito.  
  
 Pokud chcete odstranit tento problém, můžete zadat na `AREA` – direktiva `ALIGN` atribut, který je rovna nebo větší než požadované zarovnání.  
  
```  
  
AREA |.myarea1|  
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed  
  
AREA |.myarea2|,ALIGN=3  
ALIGN 8           ; OK  
  
```  
  
 A4508: Použití této otočený konstanta je zastaralé.  
 V režimu ARM je alternativní syntaxe pro určení konstanty.  Místo psaní `#<const>`, můžete napsat `#<byte>,#<rot>`, která představuje konstantní hodnota, která se získala při otáčení hodnota `<byte>` přímo pomocí `<rot>`.  V některých kontextech ARM se nepoužívá použití těchto otočený konstanty. V těchto případech použijte základní `#<const>` syntaxe místo.  
  
```  
  
ANDS r0, r0, #1                ; OK  
ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated  
  
```  
  
 A4509: Tato forma podmíněného instrukce je zastaralý.  
 Tato forma podmíněného instrukce je zastaralá ve ARM v architektuře ARMv8. Doporučujeme vám, že změníte kód, který použije větve podmíněného. Pokud chcete zobrazit, které podmíněného pokyny jsou stále podporovány, naleznete [ARM architektura referenční příručce](http://go.microsoft.com/fwlink/p/?linkid=246464).  
  
 Toto upozornění není vygenerované při `-oldit` je použít přepínač příkazového řádku.  
  
```  
  
ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Reference k příkazovému řádku assembleru ARM](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [Direktivy assembleru ARM](../../assembler/arm/arm-assembler-directives.md)