---
title: Chyba linkerů LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: fe64eecfbc9fed57c3748afd5804b76d6e4284a4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990935"
---
# <a name="linker-tools-error-lnk1301"></a>Chyba linkerů LNK1301

Našly se LTCG moduly CLR, nekompatibilní s/LTCG: parametrem.

Do linkeru byl předán modul kompilovaný s parametrem/CLR a/GL spolu s jedním z parametrů PGO (profiled Optimization)/LTCG.

Optimalizace na základě profilu nejsou pro moduly/CLR podporované.

Další informace najdete v části .

- [/GL (celková optimalizace programu)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (generování kódu během propojování)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Optimalizace na základě profilu](../../build/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Nekompilovat pomocí/CLR nebo nepropojit s jedním z parametrů PGO a/LTCG.

## <a name="example"></a>Příklad

Následující ukázka generuje LINKERŮ LNK1301:

```cpp
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```
