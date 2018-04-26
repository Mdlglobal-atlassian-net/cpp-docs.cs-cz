---
title: _putch –, _putwch – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _putwch
- _putch
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _putch
- putwch
- _putwch
dev_langs:
- C++
helpviewer_keywords:
- _putch function
- characters, writing
- putwch function
- _putwch function
- putch function
- console, writing characters to
ms.assetid: 3babc7cf-e333-405d-8449-c788d61d51aa
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c1810207b9af2cfccbd0bf9502952ad96fb9465
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="putch-putwch"></a>_putch, _putwch

Zapíše znak do konzoly.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

Vrátí *c* v případě úspěchu. Pokud **_putch –** nezdaří, vrátí **EOF**; Pokud **_putwch –** nezdaří, vrátí **weof –**.

## <a name="remarks"></a>Poznámky

Tyto funkce zápisu znak *c* přímo, bez ukládání do vyrovnávací paměti, ke konzole. V systému Windows NT **_putwch –** zapíše na aktuální nastavení národního prostředí konzoly pomocí znaků Unicode.

Verzi pomocí **jazyka _nolock** příponu jsou shodné s tím rozdílem, že nejsou chráněny z narušení jiná vlákna. Další informace najdete v tématu **_putch_nolock –**, **_putwch_nolock –**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_puttch**|**_putch**|**_putch**|**_putwch**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_putch**|\<conio.h >|
|**_putwch**|\<conio.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_getch –](getch-getwch.md).

## <a name="see-also"></a>Viz také

[I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
