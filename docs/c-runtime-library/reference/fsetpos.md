---
title: fsetpos
ms.date: 11/04/2016
api_name:
- fsetpos
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
ms.openlocfilehash: f44ab1b35c9e598f82dbc0af96979476ee353541
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956520"
---
# <a name="fsetpos"></a>fsetpos

Nastaví indikátor pozice v datovém proudu.

## <a name="syntax"></a>Syntaxe

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Ukazatel na strukturu **souborů** .

*POS*<br/>
Úložiště indikátoru pozice.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí **fsetpos** 0. Při selhání funkce vrátí nenulovou hodnotu a nastaví **errno** na jednu z následujících konstant manifestu (definované v errno. H): **EBADF**, což znamená, že soubor není přístupný nebo objekt, na který odkazuje *datový proud* , není platnou strukturou souborů; nebo **EINVAL**, což znamená, že byla předána neplatná hodnota pro *datový proud* nebo *POS* . Pokud je předán neplatný parametr, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

Další informace o těchto a dalších návratových kódech naleznete v tématech [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Funkce **fsetpos** nastaví indikátor pozice v souboru pro *datový proud* na hodnotu *POS*, která se získá v předchozím volání **fgetpos** proti *streamu*. Funkce vymaže indikátor konce souboru a zruší všechny účinky [ungetc –](ungetc-ungetwc.md) na *Stream*. Po volání **fsetpos**může být další operace na *Stream* buď Input, nebo výstup.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fgetpos](fgetpos.md).

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
