---
title: Chyba kompilátoru C2002 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b87a7fe1513c695344676624ae1968060097c885
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116916"
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