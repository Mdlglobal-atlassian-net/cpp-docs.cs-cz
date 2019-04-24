---
title: Chyba linkerů LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: 6a82d7756f1460c56d87a3d7b1360c140de19827
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160604"
---
# <a name="linker-tools-error-lnk1301"></a>Chyba linkerů LNK1301

Najde, kompatibilní s /LTCG:parameter se moduly clr LTCG.

Modul zkompilovaný s parametrem/CLR a/GL. byl předán linkeru společně s jednou z optimalizace na základě profilu (PGO) parametry parametru/LTCG.

Optimalizace na základě profilu nejsou podporovaná u modulů/CLR.

Další informace naleznete v tématu:

- [/GL (celková optimalizace programu)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (generování kódu během propojování)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Optimalizace na základě profilu](../../build/profile-guided-optimizations.md)

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