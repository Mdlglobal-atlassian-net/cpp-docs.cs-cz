---
title: Sdílení konstant
ms.date: 11/04/2016
f1_keywords:
- _SH_DENYNO
- _SH_DENYRD
- _SH_DENYRW
- _SH_DENYWR
- _SH_COMPAT
helpviewer_keywords:
- _SH_DENYRW constant
- SH_DENYRD constant
- _SH_COMPAT constant
- _SH_DENYRD constant
- SH_DENYRW constant
- sharing constants
- SH_DENYNO constant
- _SH_DENYWR constant
- SH_DENYWR constant
- _SH_DENYNO constant
- SH_COMPAT constant
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
ms.openlocfilehash: ecc7e5fc5afaf1d6d97f3ab46be3b1ed3001d8e5
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519539"
---
# <a name="sharing-constants"></a>Sdílení konstant

Konstanty pro sdílení souborů režimy.

## <a name="syntax"></a>Syntaxe

```

#include <share.h>
```

## <a name="remarks"></a>Poznámky

*Shflag* argument určuje režim sdílení, který se skládá z jednoho nebo více konstant manifestu. Ty je možné kombinovat s *oflag* argumentů (viz [konstanty souboru](../c-runtime-library/file-constants.md)).

V následující tabulce jsou uvedeny konstanty a jejich význam:

|Konstanta|Význam|
|--------------|-------------|
|`_SH_DENYRW`|Zakazuje čtení a zápis do souboru|
|`_SH_DENYWR`|Odepřít přístup pro zápis do souboru|
|`_SH_DENYRD`|Odepřít přístup pro čtení k souboru|
|`_SH_DENYNO`|Povolí čtení a zápis|
|`_SH_SECURE`|Nastaví zabezpečený režim (sdílené pro čtení, exkluzivní přístup pro zápis).|

## <a name="see-also"></a>Viz také

[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)