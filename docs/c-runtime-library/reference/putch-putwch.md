---
title: _putch, _putwch
ms.date: 11/04/2016
api_name:
- _putwch
- _putch
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
- api-ms-win-crt-conio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _putch
- putwch
- _putwch
helpviewer_keywords:
- _putch function
- characters, writing
- putwch function
- _putwch function
- putch function
- console, writing characters to
ms.assetid: 3babc7cf-e333-405d-8449-c788d61d51aa
ms.openlocfilehash: 8e7d7d57f5418e8c15aa02f015d3346298fa0422
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950047"
---
# <a name="_putch-_putwch"></a>_putch, _putwch

Zapíše znak do konzoly.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _putch(
   int c
);

wint_t _putwch(
   wchar_t c
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak, který má být výstup.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí *c* . Pokud **_putch** dojde k chybě, vrátí **EOF**. Pokud **_putwch** selžou, vrátí **WEOF**.

## <a name="remarks"></a>Poznámky

Tyto funkce zapisují znak *c* přímo bez ukládání do vyrovnávací paměti do konzoly. V systému Windows NT **_putwch** zapisuje znaky Unicode pomocí aktuálního nastavení národního prostředí konzoly.

Verze s příponou **_nolock** jsou stejné s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Další informace najdete v tématu **_putch_nolock**, **_putwch_nolock**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_puttch**|**_putch**|**_putch**|**_putwch**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_putch**|\<CONIO. h >|
|**_putwch**|\<CONIO. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_getch](getch-getwch.md).

## <a name="see-also"></a>Viz také:

[I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
