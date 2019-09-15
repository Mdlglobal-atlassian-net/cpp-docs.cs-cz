---
title: tolower, _tolower, towlower, _tolower_l, _towlower_l
ms.date: 11/04/2016
api_name:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
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
ms.openlocfilehash: 5d182fca50befac3393012572e68e65a8c81fa72
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957456"
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

*c*<br/>
Znak, který se má převést

*jazyka*<br/>
Národní prostředí, které se má použít pro překlad specifický pro národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin převede kopii *c* na malý případ, pokud je převod možný, a vrátí výsledek. Není vyhrazena žádná návratová hodnota pro indikaci chyby.

## <a name="remarks"></a>Poznámky

Každá z těchto rutin převede zadané velké písmeno na malé písmeno, pokud je to možné a důležité. Konverze velikosti **towlower** je specifická pro národní prostředí. V případě změny jsou změněny pouze znaky relevantní pro aktuální národní prostředí. Funkce bez přípony **_l** používají aktuálně nastavené národní prostředí. Verze těchto funkcí, které mají příponu **_l** , přebírají národní prostředí jako parametr a používají jej namísto aktuálně nastaveného národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Aby **_tolower** poskytovala očekávané výsledky, [__isascii](isascii-isascii-iswascii.md) a [Upper](isupper-isupper-l-iswupper-iswupper-l.md) musí vracet nenulovou hodnotu.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower**|**tolower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l** a **_towlower_l** nemají žádnou závislost národního prostředí a nejsou určeny k přímému volání. Jsou k dispozici pro interní použití v **_totlower_l**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**tolower**|\<CType. h >|
|**_tolower**|\<CType. h >|
|**towlower**|\<CType. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v tématu [funkce](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[to – funkce](../../c-runtime-library/to-functions.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
