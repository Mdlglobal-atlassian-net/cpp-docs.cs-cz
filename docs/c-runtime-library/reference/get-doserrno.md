---
title: _get_doserrno – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_doserrno
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_doserrno
- get_doserrno
dev_langs:
- C++
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba68356f13ed416a33f0bde54426ec2182e8e166
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="getdoserrno"></a>_get_doserrno

Získá hodnotu chyby, vrátí operačního systému, než je převeden do **errno** hodnotu.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_doserrno( 
   int * pValue 
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Ukazatel na celé číslo, aby byla vyplněna s aktuální hodnota **_doserrno –** globální makro.

## <a name="return-value"></a>Návratová hodnota

Pokud **_get_doserrno –** úspěšné, vrátí hodnotu nula; Pokud se nezdaří, vrátí kód chyby. Pokud *pValue* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí **einval –**.

## <a name="remarks"></a>Poznámky

**_Doserrno –** globální makro je nastaven na hodnotu nula během inicializace CRT, před proces zahájí spuštění. Je nastaven na hodnotu Chyba operačního systému vrácené žádné volání funkce úrovni systému, který vrací chybu operačního systému, a je nikdy nastaven na hodnotu nula během provádění. Při psaní kódu zkontrolujte hodnotu chyby vrácené funkcí, vždy zrušte **_doserrno –** pomocí [_set_doserrno –](set-doserrno.md) před voláním funkce. Vzhledem k tomu může dojít k přepsání jiným voláním funkce **_doserrno –**, zkontrolujte hodnotu pomocí **_get_doserrno –** ihned po volání funkce.

Doporučujeme, abyste [_get_errno –](get-errno.md) místo **_get_doserrno –** pro přenosné chybové kódy.

Možné hodnoty **_doserrno –** jsou definovány v \<errno.h >.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h >, \<cstdlib – > (C++)|\<errno.h >, \<cerrno – > (C++)|

**_get_doserrno –** je rozšíření Microsoft. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
