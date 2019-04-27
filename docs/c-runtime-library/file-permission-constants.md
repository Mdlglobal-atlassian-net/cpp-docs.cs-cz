---
title: Konstanty oprávnění souboru
ms.date: 11/04/2016
f1_keywords:
- _S_IWRITE
- _S_IREAD
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
ms.openlocfilehash: 0e042cddce6edf079aa54f114130f9750412e327
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343846"
---
# <a name="file-permission-constants"></a>Konstanty oprávnění souboru

## <a name="syntax"></a>Syntaxe

```
#include <sys/stat.h>
```

## <a name="remarks"></a>Poznámky

Jeden z následujících konstant je vyžadován v případě `_O_CREAT` (`_open`, `_sopen`) je zadán.

`pmode` Argument určuje nastavení oprávnění k souboru následujícím způsobem.

|Konstanta|Význam|
|--------------|-------------|
|`_S_IREAD`|Čtení povolené|
|`_S_IWRITE`|Zapisování povoleno|
|`_S_IREAD` &#124; `_S_IWRITE`|Čtení a zápis povolen|

Když se použije jako `pmode` argument pro `_umask`, konstanta manifestu nastaví oprávnění nastavení následujícím způsobem.

|Konstanta|Význam|
|--------------|-------------|
|`_S_IREAD`|Zápis není povolena (soubor je jen pro čtení)|
|`_S_IWRITE`|Čtení není povolena (soubor je jen pro zápis)|
|`_S_IREAD` &#124; `_S_IWRITE`|Čtení ani zápis povolen|

## <a name="see-also"></a>Viz také:

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_umask](../c-runtime-library/reference/umask.md)<br/>
[Standardní typy](../c-runtime-library/standard-types.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
