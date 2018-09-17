---
title: Použití makra NMAKE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0b68a5f3128b5d3780895f8080411819ed9b538
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712584"
---
# <a name="using-an-nmake-macro"></a>Použití makra NMAKE

Použití makra, uvést jeho názvu v závorkách předchází znak dolaru ($) následujícím způsobem.

## <a name="syntax"></a>Syntaxe

```
$(macroname)
```

## <a name="remarks"></a>Poznámky

Nejsou povoleny mezery. Závorky jsou nepovinné Pokud *makro* je jednoho znaku. Nahradí řetězec definice $(*makro*); Nedefinovaná makra je nahrazen řetězec s hodnotou null.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

[Nahrazení makra](../build/macro-substitution.md)

## <a name="see-also"></a>Viz také

[Makra a příkaz NMAKE](../build/macros-and-nmake.md)