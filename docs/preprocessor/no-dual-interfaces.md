---
title: no_dual_interfaces
ms.date: 11/04/2016
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: ae75bc2e974f374768f1a9e5a0e1ced61e9904b0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023799"
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

## <a name="see-also"></a>Viz také:

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)