---
title: Charakterizace operátoru (#@)
ms.date: 08/29/2019
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: cb2a4e07287edf5ed2d0850ec7d870c8ef307879
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218543"
---
# <a name="charizing-operator-"></a>Charakterizace operátoru (#@)

**Specifické pro společnost Microsoft**

Operátor zřetězení lze použít pouze s argumenty makra. Pokud `#@` předchází formální parametr v definici makra, je skutečný argument uzavřen v jednoduchých uvozovkách a při rozbalení makra je považován za znak. Příklad:

```cpp
#define makechar(x)  #@x
```

způsobí, že příkaz

```cpp
a = makechar(b);
```

je rozbalen na

```cpp
a = 'b';
```

Znak jednoduché uvozovky (`'`) se nedá použít s operátorem charakterizace.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)
