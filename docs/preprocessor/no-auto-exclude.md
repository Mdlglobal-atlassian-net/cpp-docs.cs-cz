---
title: no_auto_exclude
ms.date: 11/04/2016
f1_keywords:
- no_auto_exclude
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
ms.openlocfilehash: 06bde7535bd181057750ab9dd4c3999321b4990c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038939"
---
# <a name="noautoexclude"></a>no_auto_exclude
**Specifické pro C++**

Zakáže automatické vyloučení.

## <a name="syntax"></a>Syntaxe

```
no_auto_exclude
```

## <a name="remarks"></a>Poznámky

Knihovny typů mohou obsahovat definice položek definovaných v systémových hlavičkách nebo jiných knihovnách typů. `#import` se pokouší vyhnout několik chyb definice tak, že tyto položky automaticky vyloučí. Když to uděláte, [upozornění kompilátoru (úroveň 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) budou vydány pro každou položku mají být vyloučeny. Toto automatické vyloučení můžete zakázat pomocí tohoto atributu.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také:

[#import – atributy](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)