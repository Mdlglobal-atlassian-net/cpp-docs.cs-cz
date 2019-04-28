---
title: _setmaxstdio
ms.date: 11/04/2016
apiname:
- _setmaxstdio
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- setmaxstdio
- _setmaxstdio
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 58cffedf673e23a69c2d8040071b2e3353ff4502
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356339"
---
# <a name="setmaxstdio"></a>_setmaxstdio

Nastaví maximální počet souběžně otevřených souborů na **stdio** úroveň.

## <a name="syntax"></a>Syntaxe

```C
int _setmaxstdio(
   int newmax
);
```

### <a name="parameters"></a>Parametry

*newmax*<br/>
Nové maximální počet souběžně otevřených souborů na **stdio** úroveň.

## <a name="return-value"></a>Návratová hodnota

Vrátí *newmax* v případě úspěchu; jinak -1.

Pokud *newmax* je menší než **_IOB_ENTRIES** nebo novější, je vyvolána maximální počet popisovačů, které jsou k dispozici v operačním systému, obslužná rutina neplatného parametru, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce vrátí hodnotu -1 a nastaví **errno** k **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Setmaxstdio –** funkce změní hodnotu maximální počet souborů, které lze najednou otevřít v **stdio** úroveň.

Vstupně-výstupních operací C Runtime nyní podporuje mnoho otevřenější souborů na platformách Win32 než v předchozích verzích. Až 2 048 soubory lze otevřít současně [lowio úroveň](../../c-runtime-library/low-level-i-o.md) (to znamená, otevřít a získat přístup prostřednictvím **_Otevřít**, **_read**, **_write**, a tak dále řady funkcí vstupně-výstupní operace). Až 512 soubory lze otevřít současně [stdio úroveň](../../c-runtime-library/stream-i-o.md) (to znamená, otevřít a získat přístup prostřednictvím **fopen**, **fgetc –**, **fputc** a tak dále řady funkcí). Limit 512 otevřených souborů na **stdio** úroveň je možné zvýšit na maximálně 2 048 prostřednictvím **_setmaxstdio –** funkce.

Protože **stdio**– úroveň funkce, jako například **fopen**, jsou zabudovány nad **lowio** funkce, maximálně 2 048 je pevný horní mez počtu současně Otevřete soubory prostřednictvím knihovny run-time C.

> [!NOTE]
> Toto horní omezení může být rámec toho, co je podporováno konkrétní platformy Win32 a konfigurací.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Zobrazit [_getmaxstdio –](getmaxstdio.md) pro příklad použití **_setmaxstdio –**.

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
