---
title: _rmtmp – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _rmtmp
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
- rmtmp
- _rmtmp
dev_langs:
- C++
helpviewer_keywords:
- removing temporary files
- _rmtmp function
- files [C++], temporary
- rmtmp function
- files [C++], removing
- temporary files [C++], removing
ms.assetid: 7419501e-2587-4f2a-b469-0dca07f84736
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 050f1c93fc38b9fdf722682c9688336098a3da45
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405962"
---
# <a name="rmtmp"></a>_rmtmp

Odebere dočasné soubory.

## <a name="syntax"></a>Syntaxe

```C

int _rmtmp( void );
```

## <a name="return-value"></a>Návratová hodnota

**_rmtmp –** vrátí počet dočasné soubory, které se zavře a odstranit.

## <a name="remarks"></a>Poznámky

**_Rmtmp –** funkce vyčistí všechny dočasné soubory v aktuálním adresáři. Funkce odebere pouze ty soubory, které jsou vytvořené **tmpfile –**; použít pouze ve stejném adresáři, ve kterém byly vytvořeny dočasné soubory.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_rmtmp**|\<stdio.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [tmpfile –](tmpfile.md).

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_flushall](flushall.md)<br/>
[tmpfile](tmpfile.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
