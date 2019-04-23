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
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034332"
---
# <a name="charizing-operator-"></a>Charakterizace operátoru (#@)
**Microsoft Specific**

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

## <a name="see-also"></a>Viz také:

[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)