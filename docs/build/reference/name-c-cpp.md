---
title: NÁZEV (C/C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc37a96e50c6cd5bae2cc60661db04f3b92d162b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715751"
---
# <a name="name-cc"></a>NÁZEV (C/C++)

Určuje název hlavního výstupního souboru.

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>Poznámky

Ekvivalentní umožňuje zadat název výstupního souboru je [/OUT](../../build/reference/out-output-file-name.md) – možnost linkeru a ekvivalentní umožňuje nastavit základní adresu [/základní](../../build/reference/base-base-address.md) – možnost linkeru. Pokud jsou zadány oba/OUT přepisuje **název**.

Pokud vytváříte knihovnu DLL, název ovlivní pouze název knihovny DLL.

## <a name="see-also"></a>Viz také

[Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)