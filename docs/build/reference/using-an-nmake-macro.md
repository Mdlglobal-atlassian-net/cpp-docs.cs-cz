---
title: Použití makra NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: fb3b154ba8b30bbfc9a6c7c6b37720e5c60d6327
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823308"
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

[Nahrazení makra](macro-substitution.md)

## <a name="see-also"></a>Viz také:

[Makra a příkaz NMAKE](macros-and-nmake.md)
