---
title: Zástupný procedura
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: 5224fdaa2a03dc615c9e7e7bb7f7ba822a40807e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318118"
---
# <a name="stub"></a>Zástupný procedura

Při použití v souboru definice modulu, který vytváří ovladač virtuální zařízení (VxD), můžete zadat název souboru, který obsahuje strukturu IMAGE_DOS_HEADER (definované v WINNT. H) pro použití v ovladač virtuální zařízení (VxD), namísto výchozí záhlaví.

```
STUB:filename
```

## <a name="remarks"></a>Poznámky

Ekvivalentní způsob, jak určit *filename* se [/STUB](stub-ms-dos-stub-file-name.md) – možnost linkeru.

Zástupné PROCEDURY je platný v souboru definice modulu pouze při sestavování VxD.

## <a name="see-also"></a>Viz také:

[Pravidla pro příkazy definice modulu](rules-for-module-definition-statements.md)
