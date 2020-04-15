---
title: _lsearch_s
ms.date: 4/2/2020
api_name:
- _lsearch_s
- _o__lsearch_s
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
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 720b83dd48b42d77f35bce12f16e8ac79eb3b4d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341652"
---
# <a name="_lsearch_s"></a>_lsearch_s

Provede lineární hledání hodnoty. Verze [_lsearch](lsearch.md) s vylepšeními zabezpečení, jak je popsáno v [části Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

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
Objekt, který chcete vyhledat.

*base*<br/>
Ukazatel na základnu pole, které mají být prohledány.

*Číslo*<br/>
Počet prvků.

*Velikost*<br/>
Velikost každého prvku pole v bajtů.

*Porovnat*<br/>
Ukazatel na rutinu porovnání. Druhý parametr je ukazatel na klíč pro vyhledávání. Třetí parametr je ukazatel na prvek pole, který má být porovnán s klíčem.

*Kontextu*<br/>
Ukazatel na objekt, který může být přístupný ve funkci porovnání.

## <a name="return-value"></a>Návratová hodnota

Pokud je nalezen *klíč,* **_lsearch_s** vrátí ukazatel na prvek pole na *základně,* který odpovídá *klíči*. Pokud *klíč* nebyl nalezen, **_lsearch_s** vrátí ukazatel na nově přidanou položku na konci pole.

Pokud jsou funkci předány neplatné parametry, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, pak **errno** je nastavena na **EINVAL** a funkce vrátí **NULL**. Další informace naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové stavy

|*key*|*base*|*Porovnat*|*Číslo*|*Velikost*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**Null**|jakékoli|jakékoli|jakékoli|jakékoli|**EINVAL**|
|jakékoli|**Null**|jakékoli|!= 0|jakékoli|**EINVAL**|
|jakékoli|jakékoli|jakékoli|jakékoli|nula|**EINVAL**|
|jakékoli|jakékoli|**Null**|an|jakékoli|**EINVAL**|

## <a name="remarks"></a>Poznámky

Funkce **_lsearch_s** provádí lineární hledání *klíče* hodnoty v poli *číselných* prvků, každý z *šířky* bajtů. Na rozdíl od **bsearch_s** **nevyžaduje _lsearch_s** řazení pole. Pokud *klíč* nebyl nalezen, **_lsearch_s** jej přidá na konec pole a přírůstky *číslo*.

Funkce *porovnání* je ukazatel na rutinu dodanou uživatelem, která porovnává dva prvky pole a vrací hodnotu určující jejich vztah. Funkce *porovnání* také přebírá ukazatel na kontext jako první argument. **_lsearch_s** volání *porovnat* jednou nebo vícekrát během hledání, předávání ukazatelů na dva prvky pole na každé volání. *porovnat* musí porovnat prvky a pak vrátit buď nenulovou (což znamená, že prvky jsou různé) nebo 0 (což znamená, že prvky jsou identické).

Ukazatel *kontextu* může být užitečné, pokud je struktura prohledávaná data součástí objektu a funkce *porovnání* potřebuje přístup k členům objektu. Například kód ve funkci *porovnání* může přetypovat ukazatel void do příslušného typu objektu a přistupovat k členům tohoto objektu. Přidání ukazatele *kontextu* umožňuje **_lsearch_s** bezpečnější, protože další kontext lze použít, aby se zabránilo reentrancy chyby spojené s použitím statických proměnných zpřístupnit data pro *funkci porovnání.*

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Vyhledávání a řazení](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
