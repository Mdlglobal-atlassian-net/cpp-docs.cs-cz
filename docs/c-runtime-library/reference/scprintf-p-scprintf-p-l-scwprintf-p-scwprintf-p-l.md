---
title: _scprintf_p, _scprintf_p_l, _scwprintf_p, _scwprintf_p_l
ms.date: 11/04/2016
api_name:
- _scwprintf_p
- _scprintf_p_l
- _scwprintf_p_l
- _scprintf_p
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _scwprintf_p_l
- _sctprintf_p
- scprintf_p_l
- scprintf_p
- _sctprintf_p_l
- scwprintf_p
- _scprintf_p_l
- scwprintf_p_l
- _scprintf_p
- _scwprintf_p
helpviewer_keywords:
- sctprintf_p_l function
- _scwprintf_p_l function
- scprintf_p_l function
- _scprintf_p function
- _scprintf_p_l function
- scprintf_p function
- sctprintf_p function
- _scwprintf_p function
- _sctprintf_p function
- scwprintf_p function
- scwprintf_p_l function
- _sctprintf_p_l function
ms.assetid: 8390d1e1-2826-47a4-851f-6635a88087cc
ms.openlocfilehash: 79744ee814583b5b5c15fbf51d2822c6e4bfe1fa
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949488"
---
# <a name="_scprintf_p-_scprintf_p_l-_scwprintf_p-_scwprintf_p_l"></a>_scprintf_p, _scprintf_p_l, _scwprintf_p, _scwprintf_p_l

Vrátí počet znaků ve formátovaném řetězci s možností určit pořadí, ve kterém jsou parametry použity ve formátovacím řetězci.

## <a name="syntax"></a>Syntaxe

```C
int _scprintf_p(
   const char *format [,
   argument] ...
);
int _scprintf_p_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _scwprintf_p (
   const wchar_t *format [,
   argument] ...
);
int _scwprintf_p _l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>Parametry

*format*<br/>
Řetězec řízení formátu

*argument*<br/>
Volitelné argumenty

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí počet znaků, které budou vygenerovány, pokud byl řetězec vytištěn nebo odeslán do souboru nebo do vyrovnávací paměti pomocí zadaných kódů formátování. Vrácená hodnota nezahrnuje ukončující znak null. **_scwprintf_p** provádí stejnou funkci pro nejrůznější znaky.

Rozdíl mezi **_scprintf_p** a **_scprintf** je, že **_scprintf_p** podporuje poziční parametry, které umožňují určit pořadí, ve kterém jsou argumenty použity ve formátovacím řetězci. Další informace najdete v tématu [Printf_p pozičních parametrů](../../c-runtime-library/printf-p-positional-parameters.md).

Pokud je *Format* ukazatel s **hodnotou null** , je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každý *argument* (pokud existuje) je převeden podle odpovídající specifikace formátu ve *formátu*. Formát se skládá z běžných znaků a má stejnou formu a funkci jako argument *Format* pro [printf](printf-printf-l-wprintf-wprintf-l.md).

Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí vlákna.

> [!IMPORTANT]
> Ujistěte se, že *Formát* není uživatelem definovaný řetězec.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sctprintf_p**|**_scprintf_p**|**_scprintf_p**|**_scwprintf_p**|
|**_sctprintf_p_l**|**_scprintf_p_l**|**_scprintf_p_l**|**_scwprintf_p_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_scprintf_p**, **_scprintf_p_l**|\<stdio.h>|
|**_scwprintf_p**, **_scwprintf_p_l**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_scprintf, _scprintf_l, _scwprintf, _scwprintf_l](scprintf-scprintf-l-scwprintf-scwprintf-l.md)<br/>
[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
