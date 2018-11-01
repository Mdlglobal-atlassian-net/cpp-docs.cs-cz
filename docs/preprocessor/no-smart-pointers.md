---
title: no_smart_pointers
ms.date: 11/04/2016
f1_keywords:
- no_search_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: 305c08497a600f602767496cba48d108335fdeb8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636979"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**Specifické pro C++**

Potlačí vytváření inteligentních ukazatelů pro všechna rozhraní v knihovně typů.

## <a name="syntax"></a>Syntaxe

```
no_smart_pointers
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení při použití `#import`, získat deklarace inteligentního ukazatele pro všechna rozhraní v knihovně typů. Tyto inteligentní ukazatele jsou typu [třída _com_ptr_t](../cpp/com-ptr-t-class.md).

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)