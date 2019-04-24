---
title: _lsearch_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
ms.openlocfilehash: f57a96622419e3f72fc2df5b260cbbbdd59666ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156952"
---
# <a name="lsearchs"></a>_lsearch_s

Provádí lineárního hledání pro hodnotu. Verze [_lsearch –](lsearch.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*key*<br/>
Objekt pro hledání.

*base*<br/>
Ukazatel na základní pole, které chcete prohledat.

*Číslo*<br/>
Počet prvků.

*Velikost*<br/>
Velikost jednotlivých prvků pole v bajtech.

*compare*<br/>
Ukazatel na rutiny porovnání. Druhý parametr je ukazatel na klíč pro hledání. Třetí parametr je ukazatel na prvek pole k porovnání s klíči.

*context*<br/>
Ukazatel na objekt, který může přistupovat ve funkci porovnání.

## <a name="return-value"></a>Návratová hodnota

Pokud *klíč* nenajde, **_lsearch_s –** vrací ukazatel na prvek v poli *základní* , který odpovídá *klíč*. Pokud *klíč* nenajde, **_lsearch_s –** vrací ukazatel na nově přidané položky na konec pole.

Pokud jsou předány neplatné parametry pro funkci, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, pak **errno** je nastavena na **EINVAL** a funkce vrátí **NULL**. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové podmínky

|*key*|*base*|*compare*|*Číslo*|*Velikost*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NULL**|Všechny|Všechny|Všechny|Všechny|**EINVAL**|
|Všechny|**NULL**|Všechny|!= 0|Všechny|**EINVAL**|
|Všechny|Všechny|Všechny|Všechny|nula|**EINVAL**|
|Všechny|Všechny|**NULL**|Aplikace|Všechny|**EINVAL**|

## <a name="remarks"></a>Poznámky

**_Lsearch_s –** funkce provádí lineárního hledání pro hodnotu *klíč* v poli *číslo* prvky, každý z *šířka* bajtů. Na rozdíl od **bsearch_s –**, **_lsearch_s –** nevyžaduje, aby pole, který se má seřadit. Pokud *klíč* nenajde, pak **_lsearch_s –** přidá na konec objektu array a zvýší hodnotu *číslo*.

*Porovnání* funkce je ukazatel na uživatelem zadané rutinou, která porovná dva prvky pole a vrátí hodnotu určující jejich vztahu. *Porovnání* funkce také přijímá ukazatel na kontextu jako první argument. **_lsearch_s –** volání *porovnání* jednou nebo vícekrát během hledání předání ukazatele do dvou prvků pole při každém volání. *porovnání* musí porovnat prvků a vrátíte se buď nenulovou hodnotu (tj. elementy se liší), nebo 0 (tj. elementy jsou identické).

*Kontextu* ukazatele může být užitečné, pokud hledaný datová struktura je součástí objektu a *porovnání* funkce potřebuje pro přístup ke členům objektu. Například v kódu *porovnání* funkce lze přetypovat ukazatele do příslušného objektu typu a přístup členů tohoto objektu. Přidání *kontextu* díky ukazatel **_lsearch_s –** bezpečnější, protože další kontext je možné, aby se zabránilo vícenásobnému přístupu chyb spojených s použitím statické proměnné pro zpřístupnění dat pro *porovnání* funkce.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
