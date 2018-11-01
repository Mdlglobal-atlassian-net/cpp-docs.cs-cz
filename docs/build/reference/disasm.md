---
title: /DISASM
ms.date: 1/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 77f6f05029ec4480afb2180eab0bb57838d643a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462943"
---
# <a name="disasm"></a>/DISASM

Tisk zpětný překlad kódu oddílů ve výstupu DUMPBIN.

## <a name="syntax"></a>Syntaxe

> **/ DISASM**{**:**\[**BAJTŮ**|**NOBYTES**]}

### <a name="arguments"></a>Arguments

**BAJTY**<br/>
Obsahuje instrukce bajtů společně s interpretovaný operačních kódů a argumenty ve výstupu zpětný překlad. Toto je výchozí možnost.

**NOBYTES**<br/>
Nezahrnuje bajtů instrukcí ve výstupu zpětný překlad.

## <a name="remarks"></a>Poznámky

**/DISASM** možnost zobrazí zpětný překlad kódu oddílů v souboru. Pokud jsou přítomna v souboru používá symboly ladění.

**/ DISASM** by měla sloužit pouze pro nativní, ne spravované Image. Je ekvivalentní nástroj pro spravovaný kód [ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití na soubory vytvořené [/GL (celková optimalizace programu)](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)
