---
title: no_dual_interfaces
ms.date: 11/04/2016
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: d76fe3ce6bea4c3895da9d8b40d69852f912824e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466726"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**Specifické pro C++**

Změny způsobu, jakým kompilátor generuje funkce obálky pro duální rozhraní metody.

## <a name="syntax"></a>Syntaxe

```
no_dual_interfaces
```

## <a name="remarks"></a>Poznámky

Za normálních okolností se obálky volání metody prostřednictvím tabulku virtuálních funkcí pro rozhraní. S **no_dual_interfaces –**, místo volání obálky `IDispatch::Invoke` k vyvolání metody.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)