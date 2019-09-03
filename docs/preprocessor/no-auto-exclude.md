---
title: importovat atribut no_auto_exclude
ms.date: 08/29/2019
f1_keywords:
- no_auto_exclude
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
ms.openlocfilehash: 530c2b2adf24e964cb0a512371f4430a61bf8b11
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216075"
---
# <a name="no_auto_exclude-import-attribute"></a>importovat atribut no_auto_exclude

**C++Konkrétní**

Zakáže automatické vyloučení.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **no_auto_exclude**

## <a name="remarks"></a>Poznámky

Knihovny typů mohou obsahovat definice položek definovaných v systémových hlavičkách nebo jiných knihovnách typů. `#import`pokusí se zabránit více chybám definice automatickým vyloučením těchto položek. Způsobí, že se pro každou položku vyloučí [Upozornění kompilátoru (úroveň 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) . Automatické vyloučení můžete zakázat pomocí tohoto atributu.

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
