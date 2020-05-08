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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 8fa6ec1f37703ce51e0c9c565d766c56cf164322
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910183"
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

*Stream*<br/>
Ukazatel na strukturu **souborů** .

*POS*<br/>
Úložiště indikátoru pozice.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí **fsetpos** 0. Při selhání funkce vrátí nenulovou hodnotu a nastaví **errno** na jednu z následujících konstant manifestu (definované v errno. H): **EBADF**, což znamená, že soubor není přístupný nebo objekt, na který odkazuje *datový proud* , není platnou strukturou souborů; nebo **EINVAL**, což znamená, že byla předána neplatná hodnota pro *datový proud* nebo *POS* . Pokud je předán neplatný parametr, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Funkce **fsetpos** nastaví indikátor pozice v souboru pro *datový proud* na hodnotu *POS*, která se získá v předchozím volání **fgetpos** proti *streamu*. Funkce vymaže indikátor konce souboru a zruší všechny účinky [ungetc –](ungetc-ungetwc.md) na *Stream*. Po volání **fsetpos**může být další operace na *Stream* buď Input, nebo výstup.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fsetpos**|\<stdio. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fgetpos](fgetpos.md).

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
