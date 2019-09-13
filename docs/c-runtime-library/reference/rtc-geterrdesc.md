---
title: _RTC_GetErrDesc
ms.date: 11/04/2016
api_name:
- _RTC_GetErrDesc
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- RTC_GetErrDesc
- _RTC_GetErrDesc
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
ms.openlocfilehash: 7174e9242b77a904df817886df4f8c763e3e0b2c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949060"
---
# <a name="_rtc_geterrdesc"></a>_RTC_GetErrDesc

Vrátí stručný popis typu běhu pro kontrolu chyb (RTC).

## <a name="syntax"></a>Syntaxe

```C
const char * _RTC_GetErrDesc(
   _RTC_ErrorNumber errnum
);
```

### <a name="parameters"></a>Parametry

*errnum*<br/>
Číslo od 0 do 1 menší než hodnota vrácená funkcí **_RTC_NumErrors**.

## <a name="return-value"></a>Návratová hodnota

Řetězec znaků, který obsahuje krátký popis jednoho z typů chyb zjištěných systémem kontroly chyb při spuštění. Pokud je chyba menší než nula nebo větší než nebo rovna hodnotě vrácené funkcí [_RTC_NumErrors](rtc-numerrors.md), **_RTC_GetErrDesc** vrátí **hodnotu null**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_RTC_GetErrDesc**|\<rtcapi.h>|

Další informace najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[_RTC_NumErrors](rtc-numerrors.md)<br/>
[Kontrola chyb za běhu](../../c-runtime-library/run-time-error-checking.md)<br/>
