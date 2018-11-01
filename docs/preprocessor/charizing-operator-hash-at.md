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
ms.openlocfilehash: 7259487a3289173bc77517c8c616638c370041c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568337"
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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)