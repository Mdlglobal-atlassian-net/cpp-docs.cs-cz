---
title: toupper, _toupper, towupper, _toupper_l, _towupper_l
ms.date: 4/2/2020
api_name:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
- _o__toupper
- _o__toupper_l
- _o__towupper_l
- _o_toupper
- _o_towupper
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
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- towupper
- _toupper
- _totupper
- toupper
helpviewer_keywords:
- _toupper function
- towupper function
- uppercase, converting strings to
- totupper function
- string conversion, to different characters
- towupper_l function
- toupper_l function
- string conversion, case
- _toupper_l function
- _towupper_l function
- _totupper function
- case, converting
- characters, converting
- toupper function
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
ms.openlocfilehash: 85c218fdb3f5153e572e434bffbdb64510554d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362327"
---
# <a name="toupper-_toupper-towupper-_toupper_l-_towupper_l"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l

Převeďte znak na velká písmena.

## <a name="syntax"></a>Syntaxe

```C
int toupper(
   int c
);
int _toupper(
   int c
);
int towupper(
   wint_t c
);
int _toupper_l(
   int c ,
   _locale_t locale
);
int _towupper_l(
   wint_t c ,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Znak převést.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin převede kopii *c*, pokud je to možné, a vrátí výsledek.

Je-li *c* široký znak, pro který **je iswlower** nenulový a existuje odpovídající široký znak, pro který je [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) nenulová, **vrátí tažná plocha** odpovídající široký znak; jinak **vrátí tažná plocha** *c* beze změny.

Neexistuje žádná vrácená hodnota vyhrazena k označení chyby.

Aby **toupper** dát očekávané výsledky, [__isascii](isascii-isascii-iswascii.md) a [je nižší](islower-iswlower-islower-l-iswlower-l.md) musí vrátit nenulovou.

## <a name="remarks"></a>Poznámky

Každá z těchto rutin převede dané malé písmeno na velké písmeno, pokud je to možné a vhodné. Převod případu **tažné sítě** je specifický pro národní prostředí. V případě se změní pouze znaky relevantní pro aktuální národní prostředí. Funkce bez **přípony _l** používají aktuálně nastavené národní prostředí. Verze těchto funkcí s **příponou _l** převzít národní prostředí jako parametr a použít místo aktuálně nastavené národní prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Aby **toupper** dát očekávané výsledky, [__isascii](isascii-isascii-iswascii.md) a [isupper](isupper-isupper-l-iswupper-iswupper-l.md) musí oba vrátit nenulovou.

[Rutiny převodu dat](../../c-runtime-library/data-conversion.md)

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**Toupper**|**_mbctoupper**|**vlek**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l** a **_towupper_l** nemají žádnou závislost na národním prostředí a nejsou určeny k přímému volání. Jsou poskytovány pro vnitřní použití **_totupper_l**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Toupper**|\<ctype.h>|
|**_toupper**|\<ctype.h>|
|**vlek**|\<ctype.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad v [části Funkce](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Viz také

[is, isw Rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[to – funkce](../../c-runtime-library/to-functions.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
