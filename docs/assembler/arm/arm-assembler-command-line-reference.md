---
title: Referenční dokumentace pro použití nástroje assembleru ARM na příkazovém řádku
description: Referenční příručka k možnostem příkazového řádku Microsoft ARM assembleru
ms.date: 02/09/2020
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
ms.openlocfilehash: a63273e8d21e7a28574ec79d62c15f29ee59cd50
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257376"
---
# <a name="arm-assembler-command-line-reference"></a>Referenční dokumentace pro použití nástroje assembleru ARM na příkazovém řádku

Tento článek poskytuje informace z příkazového řádku pro Microsoft ARM Assembler, **armasm**. **armasm** sestaví ARMv7 jazyk pro sestavení miniatur do implementace formátu COFF (Common Object File Format) společnosti Microsoft. Linker může propojit objekty kódu COFF vytvořené pomocí rozhraní ARM Assembler i kompilátoru jazyka C. Může se propojit buď s knihovnami objektů vytvořenými pomocí Librarian.

## <a name="syntax"></a>Syntaxe

> **`armasm`** [*možnosti*] *source_file* *object_file*\
> **`armasm`** [*možnosti*] **`-o`** *object_file* *source_file*

### <a name="parameters"></a>Parametry

*možnosti*\
Kombinace nuly nebo více z následujících možností:

- **`-errors`** *název souboru*\
   Přesměruje chyby a varovné zprávy na *název souboru*.

- **`-i`** *dir*[ **`;`** <em>dir</em>] \
   Přidejte zadané adresáře do cesty pro hledání vložených souborů.

- **`-predefine`** *direktiva*\
   Pro předdefinovaný symbol zadejte direktivu SETA, SETL nebo SETS. \
   Příklad: `armasm.exe -predefine "COUNT SETA 150" source.asm`\
   Další informace najdete v [Referenční příručce k armasm kompilátoru ARM](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

- **`-nowarn`**\
   Zakáže všechny varovné zprávy.

- **`-ignore`** *Upozornění*\
   Zakáže zadané upozornění. Možné hodnoty najdete v části o upozorněních.

- **`-help`**\
   Vytiskněte zprávu Help příkazového řádku.

- **`-machine`** *počítač*\
   Zadejte typ počítače, který se má nastavit v hlavičce PE.  Možné hodnoty pro *počítač* : \
   **ARM**– nastaví typ počítače na IMAGE_FILE_MACHINE_ARMNT. Tato možnost je výchozí. \
   **Palec**– nastaví typ počítače na IMAGE_FILE_MACHINE_THUMB.

- **`-oldit`**\
   Vygenerujte bloky ARMv7-Style.  Ve výchozím nastavení jsou vygenerovány bloky IT kompatibilní s ARMv8.

- **`-via`** *název souboru*\
   Přečtěte si další argumenty příkazového řádku z *názvu souboru*.

- **`-16`**\
   Sestavte zdroj jako 16bitové instrukce pro palec.  Tato možnost je výchozí.

- **`-32`**\
   Sestavte zdroj jako 32 instrukcí ARM.

- **`-g`**\
   Vygeneruje ladicí informace.

- *možnost*`-errorReport:`\
   Tato možnost je zastaralá. Od Windows Vista se hlášení chyb řídí nastavením [zasílání zpráv o chybách systému Windows (WER)](/windows/win32/wer/windows-error-reporting) .

*source_file*\
Název zdrojového souboru.

*object_file*\
Název souboru objektu (Output).

## <a name="remarks"></a>Poznámky

Následující příklad ukazuje, jak používat armasm v typickém scénáři. Nejprve pomocí armasm Sestavte soubor zdrojového jazyka (. ASM) na soubor objektu (. obj). Pak použijte kompilátor C příkazového řádku CL ke kompilaci zdrojového souboru (. C) a také Určete možnost linkeru k propojení souboru objektu ARM.

```cmd
armasm myasmcode.asm -o myasmcode.obj
cl myccode.c /link myasmcode.obj
```

## <a name="see-also"></a>Viz také

[Diagnostické zprávy assembleru ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)\
[Direktivy assembleru ARM](../../assembler/arm/arm-assembler-directives.md)
