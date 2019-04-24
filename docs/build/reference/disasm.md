---
title: /DISASM
ms.date: 1/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 10e8187e896b3922438a8cf2dafa0aec4c91f904
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272058"
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

Pouze [/HEADERS](headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití na soubory vytvořené [/GL (celková optimalizace programu)](gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](dumpbin-options.md)
