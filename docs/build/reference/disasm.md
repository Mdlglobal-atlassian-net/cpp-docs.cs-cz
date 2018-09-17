---
title: / DISASM | Dokumentace Microsoftu
ms.date: 1/17/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /disasm
dev_langs:
- C++
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a5a4d930c47d2a3c2808cbd0a343c5c68de4ac9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707184"
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
