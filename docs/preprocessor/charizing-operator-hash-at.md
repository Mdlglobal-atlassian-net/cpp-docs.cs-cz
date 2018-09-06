---
title: Charakterizace operátoru (#@) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#@'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d86c49c8d7d0cda91ba2415167cc79c810a96b3d
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895302"
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