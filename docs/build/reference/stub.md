---
title: Zástupný procedura
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: fd2e7c4a3bd9fa09b88f4c3caa9b7d5b73c1ad98
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412936"
---
# <a name="stub"></a>Zástupný procedura

Při použití v souboru definice modulu, který vytváří ovladač virtuální zařízení (VxD), můžete zadat název souboru, který obsahuje strukturu IMAGE_DOS_HEADER (definované v WINNT. H) pro použití v ovladač virtuální zařízení (VxD), namísto výchozí záhlaví.

```
STUB:filename
```

## <a name="remarks"></a>Poznámky

Ekvivalentní způsob, jak určit *filename* se [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md) – možnost linkeru.

Zástupné PROCEDURY je platný v souboru definice modulu pouze při sestavování VxD.

## <a name="see-also"></a>Viz také:

[Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)
