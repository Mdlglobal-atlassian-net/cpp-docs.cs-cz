---
title: Konstanty oprávnění souboru
ms.date: 11/04/2016
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
ms.openlocfilehash: 9f6126b867e29ca37468c6ff383224a483639c78
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443273"
---
# <a name="file-permission-constants"></a>Konstanty oprávnění souboru

## <a name="syntax"></a>Syntaxe

```
#include <sys/stat.h>
```

## <a name="remarks"></a>Poznámky

Jedna z těchto konstant je vyžadována, pokud je zadána `_O_CREAT` (`_open`, `_sopen`).

Argument `pmode` určuje nastavení oprávnění souboru následujícím způsobem.

|Trvalé|Význam|
|--------------|-------------|
|`_S_IREAD`|Povolené čtení|
|`_S_IWRITE`|Zápis povolen|
|`_S_IREAD` &#124; `_S_IWRITE`|Čtení a zápis povolen|

Při použití jako argumentu `pmode` pro `_umask`konstanta manifestu nastaví nastavení oprávnění následujícím způsobem.

|Trvalé|Význam|
|--------------|-------------|
|`_S_IREAD`|Zápis není povolen (soubor je jen pro čtení).|
|`_S_IWRITE`|Čtení není povoleno (soubor je jen pro zápis)|
|`_S_IREAD` &#124; `_S_IWRITE`|Není povolené čtení ani zápis.|

## <a name="see-also"></a>Viz také

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_umask](../c-runtime-library/reference/umask.md)<br/>
[Standardní typy](../c-runtime-library/standard-types.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
