---
title: ZÁSTUPNÁ PROCEDURA | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 151d7b425a7f397a05e3a06e9d94489a0c76f899
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725111"
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