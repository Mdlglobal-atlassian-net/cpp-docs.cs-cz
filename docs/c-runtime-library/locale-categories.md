---
title: Kategorie národního prostředí
ms.date: 11/04/2016
f1_keywords:
- LC_MAX
- LC_MIN
- LC_MONETARY
- LC_TIME
- LC_NUMERIC
- LC_COLLATE
- LC_CTYPE
- LC_ALL
helpviewer_keywords:
- LC_MIN constant
- LC_MONETARY constant
- LC_CTYPE constant
- locale constants
- LC_MAX constant
- LC_ALL constant
- LC_TIME constant
- LC_NUMERIC constant
- LC_COLLATE constant
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
ms.openlocfilehash: 9c25e17f3047a88eda3a45782fc7da9f37b9452e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485836"
---
# <a name="locale-categories"></a>Kategorie národního prostředí

## <a name="syntax"></a>Syntaxe

```

#include <locale.h>

```

## <a name="remarks"></a>Poznámky

Kategorie národního prostředí jsou konstanty manifestu používané rutiny lokalizace k určení, jaká část informací o národním prostředí programu se použije. Národní prostředí odkazuje na umístění (nebo zemi nebo oblast), pro které je možné přizpůsobit některé aspekty programu. Oblasti závislé na národním prostředí patří, například formátování kalendářních dat nebo zobrazovací formát pro peněžní hodnoty.

|Kategorie národního prostředí|Části programu vliv|
|---------------------|-------------------------------|
|`LC_ALL`|Všechny chování specifické pro národní prostředí (všechny kategorie)|
|`LC_COLLATE`|Chování `strcoll` a `strxfrm` funkce|
|`LC_CTYPE`|Chování funkce zpracování znaků (s výjimkou **isdigit**, `isxdigit`, `mbstowcs`, a `mbtowc`, které nejsou ovlivněny)|
|`LC_MAX`|Stejné jako `LC_TIME`|
|`LC_MIN`|Stejné jako `LC_ALL`|
|`LC_MONETARY`|Vrácené informace o formátování měny `localeconv` – funkce|
|`LC_NUMERIC`|Znak pro rutiny formátovaného výstupu desetinné čárky (například `printf`), rutiny převodu dat a Neměnové informace o formátování vrácené `localeconv` – funkce|
|`LC_TIME`|Chování `strftime` – funkce|

Zobrazit [setlocale _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) příklad.

## <a name="see-also"></a>Viz také

[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcoll – funkce](../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)