---
title: Třída kontejneru::Erase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 368b722f03a68445ddd016705aa8bebc6f33e6f5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842609"
---
# <a name="container-classerase"></a>Třída kontejneru::erase

> [!NOTE]
> Toto téma se v dokumentaci k Visual C++ jako funkční příklad kontejnery použít ve standardní knihovně C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

Vymaže elementu.

## <a name="syntax"></a>Syntaxe

```

    iterator erase(
    iterator _Where);

iterator erase(
    iterator first,
    iterator last);
```

## <a name="remarks"></a>Poznámky

Odebere první členská funkce elementu řízené sekvenci, na kterou odkazuje *_Where*. Druhý členská funkce odebere elementy řízené sekvenci v rozsahu [`first`, `last`). Obě vrací iterátor, který označí první prvek zbývající nad rámec všechny elementy odebrán, nebo [end](../standard-library/container-class-end.md) Pokud neexistuje žádný takový prvek.

Členské funkce vyvolat výjimku pouze v případě, že operace kopírování vyvolá výjimku.

## <a name="see-also"></a>Viz také

[Ukázkový kontejner – třída](../standard-library/sample-container-class.md)<br/>
