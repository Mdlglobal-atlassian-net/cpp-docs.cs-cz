---
title: Třída kontejneru::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: 2c2b87e8cc51248fd3d29df7f361fff92da72957
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62210841"
---
# <a name="container-classswap"></a>Třída kontejneru::swap

> [!NOTE]
> Toto téma je v dokumentaci k Visual C++ jako funkční příklad kontejnery používané ve standardní knihovně jazyka C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

Zamění řízené sekvence mezi  **\*to** a argumentem.

## <a name="syntax"></a>Syntaxe

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>Poznámky

Pokud  **\*this.get\_alokátoru ==** _správné_**.get_allocator**, provádí odkládacího souboru v konstantním času. V opačném případě provede několik element přiřazení a volání konstruktoru je přímo úměrný počtu prvků v dané dvě řízené sekvence.

## <a name="see-also"></a>Viz také:

[Ukázkový kontejner – třída](../standard-library/sample-container-class.md)<br/>
