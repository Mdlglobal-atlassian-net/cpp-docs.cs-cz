---
title: /DISASM
ms.date: 01/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: fb394b2266470e77c50ce5398aea961c37ac34fb
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927723"
---
# <a name="disasm"></a>/DISASM

Vytiskne zpětný překlad částí kódu ve výstupu DUMPBIN.

## <a name="syntax"></a>Syntaxe

> **/DISASM** { **:** \[BAJTŮV|BAJTECH **]}**

### <a name="arguments"></a>Arguments

**PSANÝ**<br/>
Zahrnuje bajty instrukcí spolu s interpretací operačních kódů a argumentů ve výstupu zpětného překladu. Toto je výchozí možnost.

**POČET BAJTŮ**<br/>
Nezahrnuje bajty instrukcí ve výstupu zpětného překladu.

## <a name="remarks"></a>Poznámky

Možnost **/DISASM** zobrazí zpětný překlad částí kódu v souboru. Používá symboly ladění, pokud jsou k dispozici v souboru.

**/DISASM** by mělo být použito pouze pro nativní, nespravované, image. Ekvivalentní nástroj pro spravovaný kód je [Ildasm](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Pouze možnost [/Headers](headers.md) DUMPBIN je k dispozici pro soubory vytvořené pomocí možnosti kompilátoru [/GL (celý program optimalizace celého programu)](gl-whole-program-optimization.md) .

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](dumpbin-options.md)
