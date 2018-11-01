---
title: include()
ms.date: 10/18/2018
f1_keywords:
- include()
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
ms.openlocfilehash: 8f3227ba49cc0928fec5d5917efcd8869982d94a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599742"
---
# <a name="include"></a>include()

**Specifické pro C++**

Zakáže automatické vyloučení.

## <a name="syntax"></a>Syntaxe

```
include("Name1"[,"Name2", ...])
```

### <a name="parameters"></a>Parametry

*Name1*<br/>
První položky mají být nuceně zahrnuty.

*Name2*<br/>
Druhá položka mají být nuceně zahrnuty (v případě potřeby).

## <a name="remarks"></a>Poznámky

Knihovny typů mohou obsahovat definice položek definovaných v systémových hlavičkách nebo jiných knihovnách typů. `#import` se pokouší vyhnout několik chyb definice tak, že tyto položky automaticky vyloučí. Pokud byly vyloučeny položky, jak je uvedeno ve [upozornění kompilátoru (úroveň 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), a neměl by mít byl tento atribut je možné zakázat automatické vyloučení. Tento atribut může přijmout libovolný počet argumentů, každý se název knihovny typů položky mají být zahrnuty.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)