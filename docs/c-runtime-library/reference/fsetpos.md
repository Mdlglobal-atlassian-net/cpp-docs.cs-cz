---
title: fsetpos
ms.date: 4/2/2020
api_name:
- fsetpos
- _o_fsetpos
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fsetpos
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
ms.openlocfilehash: 22b8cebd0154c0dbfc3d21843380ebc9a139059a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345723"
---
# <a name="fsetpos"></a>fsetpos

Nastaví indikátor polohy datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>Parametry

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

*Pos*<br/>
Skladování indikátoru polohy.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, **vrátí funkce fsetpos** hodnotu 0. Při selhání funkce vrátí nenulovou hodnotu a nastaví **errno** na jednu z následujících konstant manifestu (definované v ERRNO. H): **EBADF**, což znamená, že soubor není přístupný nebo objekt, na který *stream* odkazuje, není platnou strukturou souboru; nebo **EINVAL**, což znamená, že byla předána neplatná hodnota pro *datový proud* nebo *pos.* Pokud je předán neplatný parametr, tyto funkce vyvolat neplatný parametr obslužné rutiny, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

Další informace o těchto a dalších návratových kódech naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

Funkce **fsetpos** nastaví indikátor pozice souboru pro *datový proud* na hodnotu *pos*, která je získána v předchozím volání **fgetpos** proti *proudu*. Funkce vymaže indikátor konce souboru a vrátit se k odstranění všech účinků [ungetc](ungetc-ungetwc.md) na *stream*. Po volání **fsetpos**, další operace na *datovém proudu* může být buď vstup nebo výstup.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [fgetpos](fgetpos.md).

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
