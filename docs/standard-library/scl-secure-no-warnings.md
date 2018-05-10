---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
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
ms.openlocfilehash: ec02ce5aab3d8a7f95ec9020fe3e2a00c1f5bef7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

Volání metod potenciálně nebezpečného ve standardní knihovně C++ výsledkem [upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Chcete-li zakázat toto upozornění, definujte makro **_SCL_SECURE_NO_WARNINGS** ve vašem kódu:

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

Pokud používáte předkompilovaných hlaviček, uveďte tato direktiva v předkompilovaný hlavičkový soubor předtím, než je zahrnout všechny běhové knihovny jazyka C nebo standardní knihovna hlavičky. Pokud jste ji vložili do souboru kódu jednotlivé zdrojové předtím, než zahrnete předkompilovaný hlavičkový soubor, je ignorován v kompilátoru.

## <a name="remarks"></a>Poznámky

Další způsoby, jak zakázat upozornění C4996 patří:

- Pomocí [/D (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md) – možnost kompilátoru:

   > cl myfile.cpp /D_SCL_SECURE_NO_WARNINGS [Další možnosti kompilátoru]

- Pomocí [/w](../build/reference/compiler-option-warning-level.md) – možnost kompilátoru:

   > cl /wd4996 [Další možnosti kompilátoru] myfile.cpp

- Pomocí [#pragma – upozornění](../preprocessor/warning.md) – direktiva:

   ```cpp
   #pragma warning(disable:4996)
   ```

Navíc můžete ručně změnit úroveň upozornění C4996 s **/w\<l >\<n >** – možnost kompilátoru. Chcete-li například nastavit upozornění C4996 na úroveň 4:

> cl /w44996 [Další možnosti kompilátoru] myfile.cpp

Další informace najdete v tématu [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, nebo jsme /wo, /Wv, wdn (úroveň upozornění)](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Viz také

[Bezpečné knihovny: standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
