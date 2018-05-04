---
title: / DISASM | Microsoft Docs
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
ms.openlocfilehash: 89b0784ff10e7d9521351e01d8907c963c9304fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="disasm"></a>/DISASM

Zpětný překlad kódu oddílů ve výstupu DUMPBIN tisku.

## <a name="syntax"></a>Syntaxe

> **/ DISASM**{**:**\[**BAJTŮ**|**NOBYTES**]}  

### <a name="arguments"></a>Arguments

**BAJTY**  
Obsahuje instrukce bajtů společně s interpretovaný operační kódy a argumenty ve výstupu zpětný překlad. Toto je výchozí možnost.

**NOBYTES**  
Nezahrnuje instrukce bajtů ve výstupu zpětný překlad.

## <a name="remarks"></a>Poznámky

**/DISASM** možnost zobrazí zpětný překlad kódu oddílů, které jsou v souboru. Pokud jsou přítomna v souboru používá ladicími symboly.

**/ DISASM** musí být použit pouze na nativní, nejsou spravované, bitové kopie. Nástroj ekvivalentní pro spravovaný kód je [ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití na soubory vyprodukované [/GL (celková optimalizace programu)](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)  
