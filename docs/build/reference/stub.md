---
title: Zástupný procedura
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: 95f8e1584bdd87f23e87c27418c0debca5c3181a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533715"
---
# <a name="stub"></a>Zástupný procedura

Při použití v souboru definice modulu, který vytváří ovladač virtuální zařízení (VxD), můžete zadat název souboru, který obsahuje strukturu IMAGE_DOS_HEADER (definované v WINNT. H) pro použití v ovladač virtuální zařízení (VxD), namísto výchozí záhlaví.

```
STUB:filename
```

## <a name="remarks"></a>Poznámky

Ekvivalentní způsob, jak určit *filename* se [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md) – možnost linkeru.

Zástupné PROCEDURY je platný v souboru definice modulu pouze při sestavování VxD.

## <a name="see-also"></a>Viz také

[Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)