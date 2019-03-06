---
title: NÁZEV (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: c4888b8f9b6dba4b826f2ee7dda7529a4bdf1586
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414496"
---
# <a name="name-cc"></a>NÁZEV (C/C++)

Určuje název hlavního výstupního souboru.

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>Poznámky

Ekvivalentní umožňuje zadat název výstupního souboru je [/OUT](../../build/reference/out-output-file-name.md) – možnost linkeru a ekvivalentní umožňuje nastavit základní adresu [/základní](../../build/reference/base-base-address.md) – možnost linkeru. Pokud jsou zadány oba/OUT přepisuje **název**.

Pokud vytváříte knihovnu DLL, název ovlivní pouze název knihovny DLL.

## <a name="see-also"></a>Viz také:

[Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)
