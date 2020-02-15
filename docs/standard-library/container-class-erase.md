---
title: Třída kontejneru::erase
ms.date: 11/04/2016
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
ms.openlocfilehash: 1fa3fe7dee10f3033b84a671fdc35c193cd6ec3c
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257894"
---
# <a name="container-classerase"></a>Třída kontejneru::erase

> [!NOTE]
> Toto téma se nachází v dokumentaci C++ společnosti Microsoft jako nefunkční příklad kontejnerů použitých ve C++ standardní knihovně. Další informace najdete v tématu [ C++ standardní kontejnery knihovny](../standard-library/stl-containers.md).

Vymaže element.

## <a name="syntax"></a>Syntaxe

```cpp
iterator erase(
    iterator _Where);

iterator erase(
    iterator first,
    iterator last);
```

## <a name="remarks"></a>Poznámky

První členská funkce odstraní prvek řízené sekvence, na kterou ukazuje *_Where*. Druhá členská funkce odstraní prvky řízené sekvence v rozsahu [`first`, `last`). Vrátí iterátor, který určí první prvek zbývající za odebranými prvky, nebo [ukončí](../standard-library/container-class-end.md) , pokud žádný takový prvek neexistuje.

Členské funkce vyvolávají výjimku pouze v případě, že operace kopírování vyvolá výjimku.

## <a name="see-also"></a>Viz také

[Ukázkový kontejner – třída](../standard-library/sample-container-class.md)
