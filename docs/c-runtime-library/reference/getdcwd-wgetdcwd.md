---
title: _getdcwd, _wgetdcwd
ms.date: 11/04/2016
apiname:
- _getdcwd
- _wgetdcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
ms.openlocfilehash: 9f6ae99ae74bb21c9462abcb37e466d63b86f8af
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501032"
---
# <a name="_getdcwd-_wgetdcwd"></a>_getdcwd, _wgetdcwd

Načte úplnou cestu k aktuálnímu pracovnímu adresáři na zadané jednotce.

## <a name="syntax"></a>Syntaxe

```C
char *_getdcwd(
   int drive,
   char *buffer,
   int maxlen
);
wchar_t *_wgetdcwd(
   int drive,
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>Parametry

*drive*<br/>
Nezáporné celé číslo, které určuje jednotku (0 = výchozí jednotka, 1 = A, 2 = B a tak dále).

Pokud není zadaná jednotka k dispozici nebo druh jednotky (například vyměnitelná, pevná, CD-ROM, disk RAM nebo síťová jednotka) nelze určit, je vyvolána obslužná rutina neplatného parametru. Další informace najdete v tématu [ověření parametru](../../c-runtime-library/parameter-validation.md).

*vyrovnávací paměti*<br/>
Umístění úložiště pro cestu nebo **hodnota null**.

Je-li zadána **hodnota null** , tato funkce přidělí vyrovnávací paměť alespoň *MAXLEN* velikosti pomocí hodnoty\ _getdcwd a návratová hodnota je ukazatel na přidělenou vyrovnávací paměť. Vyrovnávací paměť může být uvolněna voláním **Free** a předáním ukazatele.

*maxlen*<br/>
Nenulové kladné celé číslo, které určuje maximální délku cesty, ve znacích: **char** pro **_getdcwd** a **wchar_t** pro **_wgetdcwd**.

Pokud je *MAXLEN* menší nebo rovno nule, je vyvolána obslužná rutina neplatného parametru. Další informace najdete v tématu [ověření parametru](../../c-runtime-library/parameter-validation.md).

## <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec, který představuje úplnou cestu aktuálního pracovního adresáře na zadané jednotce nebo **hodnotu null**, což označuje chybu.

Pokud je *vyrovnávací paměť* zadána **jako null** a není dostatek paměti k přidělení *MAXLEN* znaků, dojde k chybě a **errno** je nastaven na **ENOMEM**. Pokud délka cesty včetně ukončujícího znaku null přesáhne *MAXLEN*, dojde k chybě a **errno** je nastaven na **ERANGE**. Další informace o těchto kódech chyb naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_getdcwd** získá úplnou cestu k aktuálnímu pracovnímu adresáři na zadané jednotce a uloží ji do *vyrovnávací paměti*. Pokud je aktuální pracovní adresář nastaven na kořen, řetězec končí zpětným lomítkem (\\). Pokud je aktuální pracovní adresář nastaven na jiný adresář než kořenový, řetězec končí názvem adresáře, nikoli zpětným lomítkem.

**_wgetdcwd** je verze **_getdcwd**s libovolným znakem a její parametr *vyrovnávací paměti* a návratová hodnota jsou řetězce s řetězci s velkým počtem znaků. V opačném případě se **_wgetdcwd** a **_getdcwd** chovají stejně.

Tato funkce je bezpečná pro přístup z více vláken, i když je závislá na **GetFullPathName**, která sama o sobě není bezpečná pro přístup z více vláken. Nicméně je možné porušit bezpečnost vlákna, pokud aplikace s více vlákny volá tuto funkci i [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew).

Verze této funkce, která má příponu **_nolock** , se chová stejně jako tato funkce s tím rozdílem, že není bezpečná pro přístup z více vláken a není chráněna před rušením jinými vlákny. Další informace najdete v tématu [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md).

Pokud jsou definovány **_DEBUG** a **_CRTDBG_MAP_ALLOC** , volání **_getdcwd** a **_wgetdcwd** jsou nahrazena voláními **_getdcwd_dbg** a **_wgetdcwd_dbg** , aby bylo možné ladit přidělování paměti. Další informace najdete v tématu[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getdcwd**|\<Direct. h >|
|**_wgetdcwd**|\<Direct. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_getdrive](getdrive.md).

## <a name="see-also"></a>Viz také:

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
