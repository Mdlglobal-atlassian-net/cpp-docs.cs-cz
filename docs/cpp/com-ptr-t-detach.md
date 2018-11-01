---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: affaefd8af4802836733587af62977171ba01410
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537797"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach

**Specifické pro Microsoft**

Extrahuje a vrátí zapouzdřený ukazatel rozhraní.

## <a name="syntax"></a>Syntaxe

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>Poznámky

Extrahuje a vrátí zapouzdřený ukazatel rozhraní a poté vyčistí úložiště zapouzdřeného ukazatele na hodnotu NULL. Tím je ukazatel rozhraní vyjmut ze zapouzdření. Je na vás volat `Release` na Vrácený ukazatel rozhraní.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)