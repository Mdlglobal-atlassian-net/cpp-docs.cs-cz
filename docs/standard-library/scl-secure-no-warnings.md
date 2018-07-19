---
title: _SCL_SECURE_NO_WARNINGS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b24012825b883550de6f58e6ce2d53b826f746ca
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965497"
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
