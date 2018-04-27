---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5dec19d4c7d6f1def451f7f11588f303961cc5c0
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
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
