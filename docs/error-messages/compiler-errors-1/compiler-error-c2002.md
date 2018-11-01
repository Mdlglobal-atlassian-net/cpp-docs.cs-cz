---
title: Chyba kompilátoru C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: 30f472aa7a9475a19eea0e92fe5c2ea0d54e382b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442845"
---
# <a name="compiler-error-c2002"></a>Chyba kompilátoru C2002

Neplatná konstanta širokých znaků

Vícebajtová znaková konstanta není platná.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Konstanta širokého znaku obsahuje více bajtů, než se očekávalo.

1. Standardní hlavička STDDEF.h není zahrnut.

1. Široké znaky se nedají zřetězit. s běžným řetězcovými literály.

1. Konstantu širokého znaku musí následovat po znaku "L":

    ```
    L'mbconst'
    ```

1. Microsoft C++ musí být text argumenty direktivy preprocesoru ASCII. Například směrnice `#pragma message(L"string")`, není platný.