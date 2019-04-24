---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: affaefd8af4802836733587af62977171ba01410
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154958"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach

**Microsoft Specific**

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