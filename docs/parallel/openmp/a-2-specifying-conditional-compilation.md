---
title: A.2   Nastavení podmíněné kompilace
ms.date: 11/04/2016
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
ms.openlocfilehash: 92ae22ffac1b1a1c3fc45a9a7a883203ff6d251e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491218"
---
# <a name="a2---specifying-conditional-compilation"></a>A.2   Nastavení podmíněné kompilace

Následující příklady ilustrují použití podmíněné kompilace OpenMP – makro `_OPENMP` ([části 2.2](../../parallel/openmp/2-2-conditional-compilation.md) na stránce 8). S OpenMP kompilace `_OPENMP` stane definice makra.

```
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

Defined – operátor preprocesoru umožňuje více než jedno makro má být testována v jedné – direktiva.

```
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```