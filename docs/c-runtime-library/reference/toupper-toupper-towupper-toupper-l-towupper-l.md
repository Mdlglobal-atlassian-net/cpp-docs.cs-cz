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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 943b66bf03420dc707415fd5da0ddf8cc3107d85
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913872"
---
# <a name="toupper-_toupper-towupper-_toupper_l-_towupper_l"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l

Převod znaku na velká písmena.

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

*r*<br/>
Znak, který se má převést

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin převede kopii *jazyka c*, je-li to možné, a vrátí výsledek.

V případě, že *c* je velký znak, pro který je **iswlower** nenulový a existuje odpovídající velký znak, pro který [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) je nenulový, **towupper** vrátí odpovídající velký znak; v opačném případě **towupper** vrátí *c* beze změny.

Není vyhrazena žádná návratová hodnota pro indikaci chyby.

Chcete-li, aby atribut **ToUpper** poskytoval očekávané výsledky, [__isascii](isascii-isascii-iswascii.md) a [Lower](islower-iswlower-islower-l-iswlower-l.md) musí vracet nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

Každá z těchto rutin převede zadané malé písmeno na velké písmeno, pokud je to možné a vhodné. Konverze velikosti **towupper** je specifická pro národní prostředí. V případě změny jsou změněny pouze znaky relevantní pro aktuální národní prostředí. Funkce bez přípony **_l** používají aktuálně nastavené národní prostředí. Verze těchto funkcí s příponou **_l** přebírají národní prostředí jako parametr a používají jej namísto aktuálně nastaveného národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Chcete-li, aby příkaz **ToUpper** poskytoval očekávané výsledky, [__isascii](isascii-isascii-iswascii.md) a v [horní](isupper-isupper-l-iswupper-iswupper-l.md) části musí vracet nenulovou hodnotu.

[Rutiny převodu dat](../../c-runtime-library/data-conversion.md)

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**ToUpper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l** a **_towupper_l** nemají žádnou závislost národního prostředí a nejsou určeny k přímému volání. Jsou k dispozici pro interní použití **_totupper_l**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ToUpper**|\<CType. h>|
|**_toupper**|\<CType. h>|
|**towupper**|\<CType. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v tématu [funkce](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Viz také

[je, rutiny ISW](../../c-runtime-library/is-isw-routines.md)<br/>
[to – funkce](../../c-runtime-library/to-functions.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
