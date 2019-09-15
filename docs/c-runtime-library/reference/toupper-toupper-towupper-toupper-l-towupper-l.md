---
title: toupper, _toupper, towupper, _toupper_l, _towupper_l
ms.date: 11/04/2016
api_name:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
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
ms.openlocfilehash: e17f139789b2c37292764f2e4508b59cddd2c03e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957907"
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

*c*<br/>
Znak, který se má převést

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin převede kopii *jazyka c*, je-li to možné, a vrátí výsledek.

V případě, že *c* je velký znak, pro který je **iswlower** nenulový a existuje odpovídající velký znak, pro který [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) je nenulový, **towupper** vrátí odpovídající velký znak; v opačném případě **towupper** vrátí *c* beze změny.

Není vyhrazena žádná návratová hodnota pro indikaci chyby.

Chcete-li, aby atribut **ToUpper** poskytoval očekávané výsledky, [__isascii](isascii-isascii-iswascii.md) a [Lower](islower-iswlower-islower-l-iswlower-l.md) musí vracet nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

Každá z těchto rutin převede zadané malé písmeno na velké písmeno, pokud je to možné a vhodné. Konverze velikosti **towupper** je specifická pro národní prostředí. V případě změny jsou změněny pouze znaky relevantní pro aktuální národní prostředí. Funkce bez přípony **_l** používají aktuálně nastavené národní prostředí. Verze těchto funkcí s příponou **_l** přebírají národní prostředí jako parametr a používají jej namísto aktuálně nastaveného národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

**Aby mohla tato** hodnota vracet očekávané výsledky, [__isascii](isascii-isascii-iswascii.md) a [Upper](isupper-isupper-l-iswupper-iswupper-l.md) musí vracet nenulovou hodnotu.

[Rutiny převodu dat](../../c-runtime-library/data-conversion.md)

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**ToUpper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l** a **_towupper_l** nemají žádnou závislost národního prostředí a nejsou určeny k přímému volání. Jsou k dispozici pro interní použití v **_totupper_l**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ToUpper**|\<CType. h >|
|**_toupper**|\<CType. h >|
|**towupper**|\<CType. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v tématu [funkce](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Viz také:

[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[to – funkce](../../c-runtime-library/to-functions.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
