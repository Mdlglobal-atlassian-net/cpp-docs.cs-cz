---
title: fsetpos – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c381cf478a97d47efe10c68096fffe3d9fd8efdf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399306"
---
# <a name="fsetpos"></a>fsetpos

Nastaví datový proud pozice indikátoru.

## <a name="syntax"></a>Syntaxe

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>Parametry

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

*POS*<br/>
Označení pozice úložiště.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného **fsetpos –** vrátí hodnotu 0. Funkce vrátí nenulovou hodnotu, při selhání a nastaví **errno** na jednu z následujících manifest konstanty (definovanou v kód chyby. H): **ebadf –**, což znamená, že soubor není dostupný nebo objekt, *datového proudu* body není platný soubor struktura; nebo **einval –**, což znamená neplatnou hodnotu pro *datového proudu* nebo *pos* byl předán. Pokud není předán neplatný parametr v těchto funkcí vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratové kódy.

## <a name="remarks"></a>Poznámky

**Fsetpos –** funkce nastaví indikátor pozice souboru pro *datového proudu* na hodnotu *pos*, který byl získán v předchozí výzvy k **fgetpos –** proti *datového proudu*. Funkce vymaže indikátoru end souboru a vrátí zpět důsledky [ungetc –](ungetc-ungetwc.md) na *datového proudu*. Po volání **fsetpos –**, další operace na *datového proudu* může být buď vstup nebo výstup.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fgetpos –](fgetpos.md).

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
