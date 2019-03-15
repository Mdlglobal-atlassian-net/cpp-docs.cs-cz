---
title: NÁZEV (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: d0813befc622db72e095c449794405fc5d58465b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812184"
---
# <a name="name-cc"></a>NÁZEV (C/C++)

Určuje název hlavního výstupního souboru.

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>Poznámky

Ekvivalentní umožňuje zadat název výstupního souboru je [/OUT](out-output-file-name.md) – možnost linkeru a ekvivalentní umožňuje nastavit základní adresu [/základní](base-base-address.md) – možnost linkeru. Pokud jsou zadány oba/OUT přepisuje **název**.

Pokud vytváříte knihovnu DLL, název ovlivní pouze název knihovny DLL.

## <a name="see-also"></a>Viz také:

[Pravidla pro příkazy definice modulu](rules-for-module-definition-statements.md)
