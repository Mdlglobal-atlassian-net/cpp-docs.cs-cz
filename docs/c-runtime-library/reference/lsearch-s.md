---
title: _lsearch_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _lsearch_s
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _lsearch_s
- lsearch_s
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21d2aface59c4c2fd4247d299af26c63cdf46d45
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="lsearchs"></a>_lsearch_s

Provede lineárního hledání pro hodnotu. Verzi [_lsearch –](lsearch.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
void *_lsearch_s(
   const void *key,
   void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Objekt, který chcete vyhledat.

*base*<br/>
Ukazatel na základní pole má proběhnout.

*Číslo*<br/>
Počet elementů.

*Velikost*<br/>
Velikost jednotlivých prvků pole v bajtech.

*compare*<br/>
Ukazatel na rutiny porovnání. Druhý parametr je ukazatel na klíč pro vyhledávání. Třetí parametr není ukazatel na element pole, který se má porovnat s klíčem.

*Kontext*<br/>
Ukazatel na objekt, který může získat přístup k ve funkci porovnání.

## <a name="return-value"></a>Návratová hodnota

Pokud *klíč* nenajde, **_lsearch_s –** vrací ukazatel na element pole v *základní* odpovídající *klíč*. Pokud *klíč* není nalezen, **_lsearch_s –** vrací ukazatel na nově přidané položky na konci tohoto pole.

Pokud jsou předány neplatné parametry pro funkce, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, pak je povoleno spuštění **errno** je nastaven na **einval –** a funkce vrátí hodnotu **NULL**. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové stavy

|*Klíč*|*base*|*compare*|*Číslo*|*Velikost*|**Kód chyby**|
|-----------|------------|---------------|-----------|------------|-------------|
|**HODNOTU NULL**|všechny|všechny|všechny|všechny|**EINVAL –**|
|všechny|**HODNOTU NULL**|všechny|!= 0|všechny|**EINVAL –**|
|všechny|všechny|všechny|všechny|nula|**EINVAL –**|
|všechny|všechny|**HODNOTU NULL**|k|všechny|**EINVAL –**|

## <a name="remarks"></a>Poznámky

**_Lsearch_s –** funkce provádí lineárního hledání pro hodnotu *klíč* v pole *číslo* elementy, každý z *šířka* bajtů. Na rozdíl od **bsearch_s –**, **_lsearch_s –** nevyžaduje pole, která se má seřadit. Pokud *klíč* není nalezen, pak **_lsearch_s –** přidá na konec pole a zvýší *číslo*.

*Porovnat* funkce je ukazatel na rutiny zadanou uživatelem, který porovnává dva elementy pole a vrátí hodnotu udávající, jejich vztahu. *Porovnat* funkce také přebírá má ukazatel na kontext jako první argument. **_lsearch_s –** volání *porovnat* jeden či více krát během hledání, předávání ukazatele na dva elementy pole při každém volání. *porovnání* musí porovnat elementy a pak se vraťte buď nenulové hodnoty (tj. elementy se liší), nebo 0 (tj. elementy jsou identické).

*Kontextu* ukazatel může být užitečné, pokud je součástí objektu vyhledávaná datovou strukturu a *porovnat* funkce potřebujete přístup ke členům v objektu. Například v kódu *porovnat* funkce může odevzdat neplatný ukazatel do příslušného objektu typu a přístupu členů tohoto objektu. Přidání *kontextu* ukazatel díky **_lsearch_s –** bezpečnější, protože další kontext umožňuje vyhnout opětovné zadání chyby související s zpřístupnit data pomocí statické proměnné *porovnat* funkce.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lsearch_s**|\<Search.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
