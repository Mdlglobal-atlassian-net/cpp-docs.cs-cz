---
title: Použití makra NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: a5f0fb9b13c5d5647b8f4ee382951df6282e8d68
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415640"
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

## <a name="see-also"></a>Viz také:

[Makra a příkaz NMAKE](../build/macros-and-nmake.md)
