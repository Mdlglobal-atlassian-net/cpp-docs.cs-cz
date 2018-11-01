---
title: _SCL_SECURE_NO_WARNINGS
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
ms.openlocfilehash: 77c60aed511fc3dbbea2d74e83e36dae735dcb0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578409"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

Volání metod potenciálně nebezpečné ve standardní knihovně C++ výsledkem [upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Chcete-li zakázat toto upozornění, definujte _SCL_SECURE_NO_WARNINGS – makro ve vašem kódu:

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

Pokud použití předkompilovaných hlaviček vložte této direktivy v souboru předkompilované hlavičky teprve potom zahrňte všechny běhové knihovny jazyka C nebo hlavičky standardní knihovny. Pokud jste ji vložili na jednotlivé zdrojový soubor kódu před zahrnutím souboru předkompilované hlavičky, je ignorován kompilátory.

## <a name="remarks"></a>Poznámky

Další možnosti, jak zakázat upozornění C4996 patří:

- Použití [/D (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md) – možnost kompilátoru:

   > cl myfile.cpp /D_SCL_SECURE_NO_WARNINGS [Další možnosti kompilátoru]

- Použití [/w](../build/reference/compiler-option-warning-level.md) – možnost kompilátoru:

   > cl /wd4996 [Další možnosti kompilátoru] myfile.cpp

- Použití [varování #pragma](../preprocessor/warning.md) – direktiva:

   ```cpp
   #pragma warning(disable:4996)
   ```

Také můžete ručně změnit úroveň upozornění C4996 se **/w\<l >\<n >** – možnost kompilátoru. Chcete-li například nastavit upozornění C4996 úrovně 4:

> cl /w44996 [Další možnosti kompilátoru] myfile.cpp

Další informace najdete v tématu [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Viz také:

[Bezpečné knihovny: standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
