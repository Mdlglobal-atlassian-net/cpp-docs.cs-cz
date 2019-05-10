---
title: Třída kontejneru::erase
ms.date: 11/04/2016
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
ms.openlocfilehash: 0ef4db1c14942fc896f10095ff2331648d27c820
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221635"
---
# <a name="container-classerase"></a>Třída kontejneru::erase

> [!NOTE]
> Toto téma je v Microsoft C++ dokumentaci jako funkční příklad kontejnerů používané C++ standardní knihovny. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

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
