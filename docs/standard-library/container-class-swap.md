---
title: Třída kontejneru::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: ccf4ae6ebc3ca13a42ca950310a60e30dbb27034
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450773"
---
# <a name="container-classswap"></a>Třída kontejneru::swap

> [!NOTE]
> Toto téma se nachází v dokumentaci C++ společnosti Microsoft jako nefunkční příklad kontejnerů použitých ve C++ standardní knihovně. Další informace najdete v tématu [ C++ standardní kontejnery knihovny](../standard-library/stl-containers.md).

Prohodí kontrolované sekvence mezi  **\*tímto** a argumentem.

## <a name="syntax"></a>Syntaxe

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>Poznámky

Pokud  **\*je to.\_Get alokace = =** Right **. get_allocator**, provede záměnu v konstantním čase. V opačném případě provede několik přiřazení prvků a volání konstruktoru v poměru k počtu prvků ve dvou řízených sekvencích.

## <a name="see-also"></a>Viz také:

[Ukázkový kontejner – třída](../standard-library/sample-container-class.md)
