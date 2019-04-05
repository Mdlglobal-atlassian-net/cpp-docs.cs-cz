---
title: Charakterizace operátoru (#@)
ms.date: 11/04/2016
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: c9acc9b9872e096cd441b950632c341e975fecb8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034332"
---
# <a name="charizing-operator-"></a>Charakterizace operátoru (#@)
**Specifické pro Microsoft**

Operátor zřetězení lze použít pouze s argumenty makra. Pokud `#@` předchází formální parametr v definici makra, je skutečný argument uzavřen do jednoduchých uvozovek a při rozbalení makra je považován za znak. Příklad:

```
#define makechar(x)  #@x
```

způsobí, že příkaz

```
a = makechar(b);
```

je rozbalen na

```
a = 'b';
```

Znak jednoduchých uvozovek nelze použít spolu s operátorem zřetězení.

**END Specifické pro Microsoft**

## <a name="see-also"></a>Viz také:

[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)