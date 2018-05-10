---
title: Třída kontejneru::swap | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0ac2b3322f7f034c09c86f2307da2e3f3995c0d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="container-classswap"></a>Třída kontejneru::swap

> [!NOTE]
> Toto téma se v dokumentaci k Visual C++ jako funkční příklad kontejnery použít ve standardní knihovně C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

Prohození řízené pořadí mezi  **\*to** a jeho argumentem.

## <a name="syntax"></a>Syntaxe

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>Poznámky

Pokud  **\*this.get\_allocator ==** _správné_**.get_allocator**, provede prohození konstantní včas. Jinak provede několik element přiřazení a volá konstruktor úměrná počet elementů ve dvou řízené pořadí.

## <a name="see-also"></a>Viz také

[Ukázkový kontejner – třída](../standard-library/sample-container-class.md)<br/>
