---
title: _stat – struktura, st_mode – konstanty pole
ms.date: 11/04/2016
f1_keywords:
- S_IFCHR
- S_IFDIR
- _S_IWRITE
- S_IFMT
- _S_IFDIR
- _S_IREAD
- S_IEXEC
- _S_IEXEC
- _S_IFMT
- S_IWRITE
- S_IFREG
- S_IREAD
- _S_IFCHR
- _S_IFREG
helpviewer_keywords:
- S_IFDIR constant
- stat structure
- S_IWRITE constant
- S_IEXEC constant
- _S_IFREG constant
- S_IREAD constant
- stat structure, constants
- _S_IFMT constant
- st_mode field constants
- S_IFMT constant
- _S_IEXEC constant
- _S_IWRITE constant
- _S_IFDIR constant
- S_IFREG constant
- S_IFCHR constant
- _S_IREAD constant
- _S_IFCHR constant
ms.assetid: fd462004-7563-4766-8443-30b0a86174b6
ms.openlocfilehash: 88b81ac5450d04a5a3e617af4658bb6e73fb4dd9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502216"
---
# <a name="stat-structure-stmode-field-constants"></a>_stat – struktura, st_mode – konstanty pole

## <a name="syntax"></a>Syntaxe

```

#include <sys/stat.h>

```

## <a name="remarks"></a>Poznámky

Tyto konstanty se používají k označení typu souboru v **st_mode –** pole [_stat – struktura](../c-runtime-library/standard-types.md).

Konstanty bitové masky jsou popsané níže:

|Konstanta|Význam|
|--------------|-------------|
|`_S_IFMT`|Zadejte masku souboru.|
|`_S_IFDIR`|Adresář|
|`_S_IFCHR`|Speciální znaky (označuje zařízení, pokud je nastavení)|
|`_S_IFREG`|Pravidelné|
|`_S_IREAD`|Oprávnění ke čtení, vlastníka|
|`_S_IWRITE`|Oprávnění zapisovat, vlastníka|
|`_S_IEXEC`|Spuštění/hledání oprávnění vlastníka|

## <a name="see-also"></a>Viz také

[_stat, _wstat – funkce](../c-runtime-library/reference/stat-functions.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[Standardní typy](../c-runtime-library/standard-types.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)