---
title: / DISASM | Microsoft Docs
ms.date: 1/17/2018
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /disasm
dev_langs: C++
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d448b92c3436f3d2875bd8d9b8e0af6a7149e065
ms.sourcegitcommit: ff9bf140b6874bc08718674c07312ecb5f996463
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="disasm"></a>/DISASM

Zpětný překlad kódu oddílů ve výstupu DUMPBIN tisku.

## <a name="syntax"></a>Syntaxe

> **/DISASM**{**:**\[**BYTES**|**NOBYTES**]}  

### <a name="arguments"></a>Arguments

**BYTES**  
Obsahuje instrukce bajtů společně s interpretovaný operační kódy a argumenty ve výstupu zpětný překlad. Toto je výchozí možnost.

**NOBYTES**  
Nezahrnuje instrukce bajtů ve výstupu zpětný překlad.

## <a name="remarks"></a>Poznámky

**/DISASM** možnost zobrazí zpětný překlad kódu oddílů, které jsou v souboru. Pokud jsou přítomna v souboru používá ladicími symboly.

**/ DISASM** musí být použit pouze na nativní, nejsou spravované, bitové kopie. Nástroj ekvivalentní pro spravovaný kód je [ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití na soubory vyprodukované [/GL (celková optimalizace programu)](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)  
