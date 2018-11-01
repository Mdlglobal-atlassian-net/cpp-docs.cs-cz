---
title: Použití makra NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: 9d8ff76e1e730b65db363749797ef9ae2062adab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645078"
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