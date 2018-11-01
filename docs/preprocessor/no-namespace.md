---
title: no_namespace
ms.date: 11/04/2016
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: b17bf5fb5f44d5453de29febe001f9e8737102b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540436"
---
# <a name="nonamespace"></a>no_namespace
**Specifické pro C++**

Určuje, že název oboru názvů není generovaný kompilátorem.

## <a name="syntax"></a>Syntaxe

```
no_namespace
```

## <a name="remarks"></a>Poznámky

Obsah knihovny typů v `#import` soubor hlaviček jsou obvykle definovány v oboru názvů. Byl zadán název oboru názvů `library` příkaz v původním souboru IDL. Pokud **no_namespace** zadán atribut, pak tento obor názvů není generovaný kompilátorem.

Pokud chcete použít jiný obor názvů, použijte [rename_namespace](../preprocessor/rename-namespace.md) místo atributu.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)