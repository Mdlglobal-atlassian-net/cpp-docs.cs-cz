---
title: Třída kontejneru::Reference | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- reference method
ms.assetid: ab85a9fb-c628-4761-9a5f-a0231fad7690
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13883e1426be22c8cf3d329be33258c69511900d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966010"
---
# <a name="container-classreference"></a>Třída kontejneru::reference

> [!NOTE]
> Toto téma je v dokumentaci k Visual C++ jako funkční příklad kontejnery používané ve standardní knihovně jazyka C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

Popisuje objekt, který může sloužit jako odkaz na prvek řízené sekvence.

## <a name="syntax"></a>Syntaxe

```

typedef T2 reference;
```

## <a name="remarks"></a>Poznámky

Je popsán jako synonymum pro neurčeného typu `T2` (obvykle `Alloc::reference`). Objekt typu `reference` lze převést na objekt typu [const_reference](../standard-library/container-class-const-reference.md).

## <a name="see-also"></a>Viz také:

[Ukázkový kontejner – třída](../standard-library/sample-container-class.md)<br/>
