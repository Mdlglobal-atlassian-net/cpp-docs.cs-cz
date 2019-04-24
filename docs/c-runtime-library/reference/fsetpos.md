---
title: fsetpos
ms.date: 11/04/2016
apiname:
- fsetpos
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
- fsetpos
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
ms.openlocfilehash: 9854c71e381da6ec9a75d440b9588e2476bada7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287570"
---
# <a name="fsetpos"></a>fsetpos

Nastaví Indikátor pozice v proudu.

## <a name="syntax"></a>Syntaxe

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Ukazatel na **souboru** struktury.

*pos*<br/>
Indikátor pozice v úložišti.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného ověření **fsetpos** vrátí hodnotu 0. Při selhání, funkce vrátí nenulovou hodnotu a nastaví **errno** na jednu z následujících manifest konstanty (definované v ERRNO. H): **EBADF**, což znamená, soubor není přístupný nebo objekt, který *datového proudu* bodů není platným souborem struktury; nebo **EINVAL**, což znamená, že neplatná hodnota pro *datového proudu*  nebo *pos* byl předán. Pokud je předán neplatný parametr, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratových kódů.

## <a name="remarks"></a>Poznámky

**Fsetpos** funkce nastaví indikátor pozice v souboru pro *stream* hodnotě *pos*, získaný v předchozím volání **fgetpos**proti *stream*. Funkce vymaže indikátor konce souboru a vrátí zpět důsledky [ungetc –](ungetc-ungetwc.md) na *stream*. Po volání **fsetpos**, další operaci na *stream* může být buď vstup nebo výstup.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fgetpos](fgetpos.md).

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
