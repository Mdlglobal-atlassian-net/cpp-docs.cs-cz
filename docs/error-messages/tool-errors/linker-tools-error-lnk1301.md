---
title: Chyba Linkerů LNK1301 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1301
dev_langs:
- C++
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8646de5bb81120f6445e16b819b27da62ed9d5ec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039943"
---
# <a name="linker-tools-error-lnk1301"></a>Chyba linkerů LNK1301

Najde, kompatibilní s /LTCG:parameter se moduly clr LTCG.

Modul zkompilovaný s parametrem/CLR a/GL. byl předán linkeru společně s jednou z optimalizace na základě profilu (PGO) parametry parametru/LTCG.

Optimalizace na základě profilu nejsou podporovaná u modulů/CLR.

Další informace naleznete v tématu:

- [/GL (celková optimalizace programu)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (generování kódu během propojování)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Nejde zkompilovat s parametrem/CLR nebo nepropojovat s jeden z parametrů PGO do parametru/LTCG.

## <a name="example"></a>Příklad

Následující ukázka generuje LNK1301:

```
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```