---
title: no_namespace
ms.date: 11/04/2016
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: f6bd60de02bf0166d5cf0b0cd1bc1de56ceda5bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326557"
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

## <a name="see-also"></a>Viz také:

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)