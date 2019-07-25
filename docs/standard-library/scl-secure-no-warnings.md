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
ms.openlocfilehash: d19d47fe7120301740e1431765fc6edbeaa48c60
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448197"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

Výsledkem volání libovolné potenciálně nebezpečné metody ve standardní knihovně C++ je [Upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Chcete-li zakázat toto upozornění, definujte makro _SCL_SECURE_NO_WARNINGS v kódu:

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

Použijete-li předkompilované hlavičky, vložte tuto direktivu do souboru předkompilované hlavičky předtím, než bude zahrnuta jakákoli Knihovna modulu runtime jazyka C nebo hlavičky standardní knihovny. Pokud jej umístíte do samostatného souboru se zdrojovým kódem před zahrnutím souboru předkompilované hlavičky, kompilátor je ignoruje.

## <a name="remarks"></a>Poznámky

Mezi další způsoby, jak zakázat C4996 upozornění, patří:

- Použití možnosti kompilátoru [/d (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md) :

   > CL/D_SCL_SECURE_NO_WARNINGS [Další možnosti kompilátoru] MyFile. cpp

- Pomocí možnosti kompilátoru [/w](../build/reference/compiler-option-warning-level.md) :

   > CL/wd4996 [Další možnosti kompilátoru] MyFile. cpp

- Použití direktivy [upozornění #pragma](../preprocessor/warning.md) :

   ```cpp
   #pragma warning(disable:4996)
   ```

Také můžete ručně změnit úroveň Upozornění C4996 pomocí možnosti kompilátoru **/w\<l\<> n >** . Například pro nastavení Upozornění C4996 na úroveň 4:

> CL/w44996 [Další možnosti kompilátoru] MyFile. cpp

Další informace najdete v tématech [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Viz také:

[Bezpečné knihovny: Standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)
