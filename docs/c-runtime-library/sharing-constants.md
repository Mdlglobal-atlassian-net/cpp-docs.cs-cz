---
title: Sdílení konstant | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _SH_DENYNO
- _SH_DENYRD
- _SH_DENYRW
- _SH_DENYWR
- _SH_COMPAT
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05226ffcc5a10785391969f8162a76034efc4d92
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097300"
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