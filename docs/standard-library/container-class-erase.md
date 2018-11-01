---
title: Třída kontejneru::erase
ms.date: 11/04/2016
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
ms.openlocfilehash: 11e13fc74de779076b40ba338a21a6736eb04e06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553020"
---
# <a name="container-classerase"></a>Třída kontejneru::erase

> [!NOTE]
> Toto téma je v dokumentaci k Visual C++ jako funkční příklad kontejnery používané ve standardní knihovně jazyka C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

Odstraní prvek.

## <a name="syntax"></a>Syntaxe

```

    iterator erase(
    iterator _Where);

iterator erase(
    iterator first,
    iterator last);
```

## <a name="remarks"></a>Poznámky

První členská funkce odstraní prvek řízené sekvence, na které odkazuje *_Where*. Druhá členská funkce odebere prvky řízené sekvence v rozsahu [`first`, `last`). Oba vracejí iterátor, který určuje první prvek zbývající za všemi odstraněnými prvky, nebo [end](../standard-library/container-class-end.md) Pokud žádný takový prvek neexistuje.

Členské funkce výjimku pouze v případě, že operace kopírování dojde k výjimce.

## <a name="see-also"></a>Viz také:

[Ukázkový kontejner – třída](../standard-library/sample-container-class.md)<br/>
