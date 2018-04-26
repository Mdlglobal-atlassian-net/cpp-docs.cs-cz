---
title: _get_tzname – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_tzname
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_tzname
- get_tzname
dev_langs:
- C++
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a3a9fc2b90ac9e52a78613bc8ccfcd24b9acb56
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="gettzname"></a>_get_tzname

Načte řetězcovou reprezentaci znak název časového pásma nebo letní názvu standardního časového pásma (letní čas).

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_tzname(
    size_t* pReturnValue,
    char* timeZoneName,
    size_t sizeInBytes,
    int index
);
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Délka řetězce *timeZoneName* včetně zakončením hodnotu NULL.

*timeZoneName*<br/>
Adresa řetězec znaků pro reprezentaci název časového pásma nebo letní názvu standardního časového pásma (letní čas), v závislosti na *index*.

*sizeInBytes*<br/>
Velikost *timeZoneName* znak řetězec v bajtech.

*index*<br/>
Index jeden ze zadaných názvů dva časové pásmo pro načtení.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, jinak **errno** zadejte hodnotu.

Pokud má jedna *timeZoneName* je **NULL**, nebo *sizeInBytes* je nulová nebo menší než nula (ale ne oba), je vyvolána obslužnou rutinu neplatný parametr, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí **einval –**.

### <a name="error-conditions"></a>Chybové stavy

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|Návratová hodnota|Obsah *timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|velikost TZ název|**HODNOTU NULL**|0|0 nebo 1|0|nedojde ke změně|
|velikost TZ název|všechny|> 0|0 nebo 1|0|Název TZ|
|nedojde ke změně|**HODNOTU NULL**|> 0|všechny|**EINVAL –**|nedojde ke změně|
|nedojde ke změně|všechny|nula|všechny|**EINVAL –**|nedojde ke změně|
|nedojde ke změně|všechny|> 0|> 1|**EINVAL –**|nedojde ke změně|

## <a name="remarks"></a>Poznámky

**_Get_tzname –** funkce načte znak řetězcovou reprezentaci název časového pásma nebo letní názvu standardního časového pásma (letní čas) do adresu *timeZoneName* v závislosti na index hodnota, společně s velikost řetězce do *pReturnValue*. Pokud *timeZoneName* je **NULL** a *sizeInBytes* je nula, velikost řetězce buď časové pásmo v bajtech je vrácený v *pReturnValue*. Index hodnoty musí být buď 0 pro zónu (běžný čas) nebo 1 pro letní standardního časového pásma; všechny ostatní hodnoty indexu mít neurčená výsledky.

### <a name="index-values"></a>Index hodnoty

|*index*|Obsah *timeZoneName*|*timeZoneName* výchozí hodnota|
|-------------|--------------------------------|----------------------------------|
|0|Název časového pásma|"PST"|
|1|Název zóny letního času (běžný čas)|"PDT"|
|< 0 nebo > 1|**errno** nastavena na **einval –**|nedojde ke změně|

Pokud během doby běhu jsou explicitně změnit hodnoty, výchozí hodnoty jsou "PST" a "PDT".  Velikosti tyto znaková pole se řídí **tzname_max –** hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_tzname**|\<Time.h >|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Správa času](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[TZNAME_MAX](../../c-runtime-library/tzname-max.md)<br/>
