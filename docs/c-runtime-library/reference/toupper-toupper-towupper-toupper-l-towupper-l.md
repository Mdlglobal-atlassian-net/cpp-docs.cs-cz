---
title: toupper, _toupper, towupper, _toupper_l, _towupper_l
ms.date: 11/04/2016
apiname:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
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
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: 6dd564a27ee7f3c2bb095564e5c9423249d6babc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155495"
---
# <a name="toupper-toupper-towupper-toupperl-towupperl"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l

Převedení znaku na velká písmena.

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
Znak pro převod.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin převádí kopii *c*, pokud je to možné a vrátí výsledek.

Pokud *c* je široký znak, pro kterou **iswlower –** je nenulová a odpovídající široké znaky, pro které [iswupper –](isupper-isupper-l-iswupper-iswupper-l.md) nenulové, **towupper –** vrátí odpovídající širokého znaku; v opačném případě **towupper –** vrátí *c* beze změny.

Vyhrazená k indikaci chyby není žádnou návratovou hodnotu.

Aby **toupper** očekávané výsledky, [__isascii –](isascii-isascii-iswascii.md) a [islower](islower-iswlower-islower-l-iswlower-l.md) musí obě vrací nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

Každá z těchto rutin Pokud je to možné převede daný malým písmenem na velké písmeno a vhodné. Převod velikosti písmen **towupper –** je specifických pro národní prostředí. V případě se změní pouze znaky relevantní pro aktuální národní prostředí. Funkce bez **_l** příponu použít aktuálně nastavené národního prostředí. Verze těchto funkcí s **_l** přípona trvat národního prostředí jako parametr, který budete používat místo aktuálně nastavené národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Aby **toupper** očekávané výsledky, [__isascii –](isascii-isascii-iswascii.md) a [isupper](isupper-isupper-l-iswupper-iswupper-l.md) musí obě vrací nenulovou hodnotu.

[Rutiny převodu dat](../../c-runtime-library/data-conversion.md)

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**toupper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l –** a **_towupper_l –** mít žádnou závislost národního prostředí a neměly by být volány přímo. Jsou určeny pro interní použití rozhraním **_totupper_l**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**toupper**|\<ctype.h>|
|**_toupper**|\<ctype.h>|
|**towupper**|\<ctype.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [funkcí](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Viz také:

[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[to – funkce](../../c-runtime-library/to-functions.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
