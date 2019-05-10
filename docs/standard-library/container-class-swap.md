---
title: Třída kontejneru::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: b344747c42e9b8b751b97747aacec0b39d10d6a1
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221527"
---
# <a name="container-classswap"></a>Třída kontejneru::swap

> [!NOTE]
> Toto téma je v Microsoft C++ dokumentaci jako funkční příklad kontejnerů používané C++ standardní knihovny. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

Zamění řízené sekvence mezi  **\*to** a argumentem.

## <a name="syntax"></a>Syntaxe

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>Poznámky

Pokud  **\*this.get\_alokátoru ==** _správné_**.get_allocator**, provádí odkládacího souboru v konstantním času. V opačném případě provede několik element přiřazení a volání konstruktoru je přímo úměrný počtu prvků v dané dvě řízené sekvence.

## <a name="see-also"></a>Viz také:

[Ukázkový kontejner – třída](../standard-library/sample-container-class.md)<br/>
