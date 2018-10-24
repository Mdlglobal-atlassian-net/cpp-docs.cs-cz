---
title: Příkazový řádek referenční dokumentace assembleru ARM | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e88f35035944ee24bed0bef8733db0e2c0139c83
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685338"
---
# <a name="arm-assembler-command-line-reference"></a>Referenční dokumentace pro použití nástroje assembleru ARM v příkazovém řádku

Tento článek obsahuje informace o assembler Microsoft ARM *armasm*, které zkompiluje jazyk sestavení ARMv7 Thumb do implementace společnosti Microsoft z Common Object File Format (COFF). Propojovací program můžete propojit COFF kód s kódem v objektu, který je vytvořen assembleru ARM nebo kompilátor jazyka C, společně s objekt knihovny, které jsou vytvořené nástrojem librarian.

## <a name="syntax"></a>Syntaxe

> **armasm** [*možnosti*] *zdrojový soubor* *objectfile*
> **armasm**  [*možnosti *]  **-o**  *objectfile*  *zdrojový soubor*

### <a name="parameters"></a>Parametry

*Možnosti*<br/>
Kombinace nuly nebo více z následujících akcí:

- **-chyby** *název souboru*<br/>
   Přesměrovat chybové zprávy a upozornění na *filename*.

- **-i** *dir*[**;** <em>dir</em>]<br/>
   Přidáte do cesty hledání zahrnutí zadaných adresářích.

- **-předdefinovat** *– direktiva*<br/>
   Zadejte direktivu SETA, SETL nebo sady pro předdefinování symbol.<br/>
   Příklad: **armasm.exe-předdefinovat source.asm "COUNT SETA 150"**<br/>
   Další informace najdete v tématu [kompilátoru ARM armasm referenční příručka](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

- **-nowarn**<br/>
   Zakážete všechna upozornění.

- **-Ignorovat** *upozornění*<br/>
   Zadané upozornění vypněte. Možné hodnoty najdete v části o upozornění.

- **– Nápověda**<br/>
   Vytisknout zprávu Nápověda k příkazovému řádku.

- **-machine** *počítače*<br/>
   Zadejte typ počítače nastavit v záhlaví PE.  Možné hodnoty pro *počítač* jsou:<br/>
   **ARM**– nastaví typ počítače IMAGE_FILE_MACHINE_ARMNT. Toto nastavení je výchozí.<br/>
   **JEZDEC**– nastaví typ počítače IMAGE_FILE_MACHINE_THUMB.

- **-oldit**<br/>
   Vygenerování ARMv7 style IT bloky.  Ve výchozím nastavení jsou kompatibilní s ARMv8 IT bloky jsou generovány.

- **-prostřednictvím** *název souboru*<br/>
   Přečtěte si další argumenty příkazového řádku z *filename*.

- **-16**<br/>
   Poskládejte si zdroj jako pokyny Thumb 16 bitů.  Toto nastavení je výchozí.

- **-32**<br/>
   Poskládejte si zdroj jako 32-bit ARM pokyny.

- **-g**<br/>
   Generovat ladicí informace.

- **-errorReport:** *možnost*<br/>
   Zadejte jak interní assembler jsou hlášeny chyby do Microsoftu.  Možné hodnoty pro *možnost* jsou:<br/>
   **žádný**– Neodesílat sestavy.<br/>
   **řádek**– výzva k zprávy odesílat hned.<br/>
   **fronty**– výzva k odeslání zprávy při dalším přihlášení správce. Toto nastavení je výchozí.<br/>
   **Odeslat**– odeslání sestavy automaticky.

*zdrojový soubor*<br/>
Název zdrojového souboru.

*objectfile*<br/>
Název souboru objektu (výstup).

## <a name="remarks"></a>Poznámky

Následující příklad ukazuje, jak používat armasm v rámci typického scénáře. Nejprve pomocí armasm sestavení souboru jazyka assembleru zdroje (asm) do souboru objektů (.obj). Potom použijte cl – kompilátor příkazového řádku jazyka C pro kompilaci zdrojového (.c) a také určit možnost propojit soubor objektu ARM.

**armasm myasmcode.asm -o myasmcode.obj**

**cl myccode.c/Link myasmcode.obj**

## <a name="see-also"></a>Viz také:

[Diagnostické zprávy assembleru ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
[Direktivy assembleru ARM](../../assembler/arm/arm-assembler-directives.md)<br/>
