---
title: NÁZEV (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: c05e82409d6b6e48390d54160e8ff23ada788d41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646196"
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