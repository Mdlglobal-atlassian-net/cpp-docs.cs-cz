---
title: tolower, _tolower, towlower, _tolower_l, _towlower_l
ms.date: 11/04/2016
apiname:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: f7d017235eddb19b08353dceb332a2721e7434aa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470067"
---
# <a name="tolower-tolower-towlower-tolowerl-towlowerl"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l

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

*c*<br/>
Znak pro převod.

*Národní prostředí*<br/>
Národní prostředí pro překlad specifických pro národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin převádí kopii *c* na malá písmena, pokud převod je možné a vrátí výsledek. Vyhrazená k indikaci chyby není žádnou návratovou hodnotu.

## <a name="remarks"></a>Poznámky

Pokud je to možné a relevantní každá z těchto rutin dané velké písmeno převede na malá písmena. Převod velikosti písmen **towlower –** je specifických pro národní prostředí. V případě se změní pouze znaky relevantní pro aktuální národní prostředí. Funkce bez **_l** příponu použít aktuálně nastavené národního prostředí. Verze těchto funkcí, které mají **_l** přípona trvat národního prostředí jako parametr, který budete používat místo aktuálně nastavené národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Aby **_tolower –** očekávané výsledky, [__isascii –](isascii-isascii-iswascii.md) a [isupper](isupper-isupper-l-iswupper-iswupper-l.md) musí obě vrací nenulovou hodnotu.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower –**|**ToLower**|**_mbctolower –**|**towlower –**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l –** a **_towlower_l –** mít žádnou závislost národního prostředí a neměly by být volány přímo. Jsou určeny pro interní použití rozhraním **_totlower_l**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ToLower**|\<ctype.h >|
|**_tolower –**|\<ctype.h >|
|**towlower –**|\<ctype.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [funkcí](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[to – funkce](../../c-runtime-library/to-functions.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
