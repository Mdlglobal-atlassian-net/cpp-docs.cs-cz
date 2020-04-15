---
title: tolower, _tolower, towlower, _tolower_l, _towlower_l
ms.date: 4/2/2020
api_name:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
- _o__tolower
- _o__tolower_l
- _o__towlower_l
- _o_tolower
- _o_towlower
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
helpviewer_keywords:
- tolower_l function
- _tolower_l function
- totlower function
- string conversion, to different characters
- lowercase, converting to
- tolower function
- string conversion, case
- towlower function
- _tolower function
- _totlower function
- towlower_l function
- case, converting
- characters, converting
- _towlower_l function
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
ms.openlocfilehash: 560fde4ae2167256acd54856fced15bc6ccecae6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362364"
---
# <a name="tolower-_tolower-towlower-_tolower_l-_towlower_l"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l

Převede znak na malá písmena.

## <a name="syntax"></a>Syntaxe

```C
int tolower(
   int c
);
int _tolower(
   int c
);
int towlower(
   wint_t c
);
int _tolower_l(
   int c,
   _locale_t locale
);
int _towlower_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Znak převést.

*Národní prostředí*<br/>
Národní prostředí pro překlad y specifické pro národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin převede kopii *c* na malá písmena, pokud je převod možný, a vrátí výsledek. Neexistuje žádná vrácená hodnota vyhrazena k označení chyby.

## <a name="remarks"></a>Poznámky

Každá z těchto rutin převede dané velké písmeno na malé písmeno, pokud je to možné a relevantní. Převod případu **tažného systému** je specifický pro národní prostředí. V případě se změní pouze znaky relevantní pro aktuální národní prostředí. Funkce bez **přípony _l** používají aktuálně nastavené národní prostředí. Verze těchto funkcí, které mají **_l** příponu trvat národní prostředí jako parametr a použít místo aktuálně nastavené národní prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Aby **_tolower** poskytnout očekávané výsledky, [__isascii](isascii-isascii-iswascii.md) a [isupper](isupper-isupper-l-iswupper-iswupper-l.md) musí oba vrátit nenulovou.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower**|**Tolower**|**_mbctolower**|**tažné duštinky**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l** a **_towlower_l** nemají žádnou závislost na národním prostředí a nemají být volány přímo. Jsou poskytovány pro vnitřní použití **_totlower_l**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Tolower**|\<ctype.h>|
|**_tolower**|\<ctype.h>|
|**tažné duštinky**|\<ctype.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad v [části Funkce](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[is, isw Rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[to – funkce](../../c-runtime-library/to-functions.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
