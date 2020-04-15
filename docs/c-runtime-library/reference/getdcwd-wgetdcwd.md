---
title: _getdcwd, _wgetdcwd
ms.date: 4/2/2020
api_name:
- _getdcwd
- _wgetdcwd
- _o__getdcwd
- _o__wgetdcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 3a4ca8ff3f1153893282c65bc4c2becd687138ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344402"
---
# <a name="_getdcwd-_wgetdcwd"></a>_getdcwd, _wgetdcwd

Získá úplnou cestu aktuálního pracovního adresáře na zadané jednotce.

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

*Jednotky*<br/>
Nezáporné celé číslo, které určuje jednotku (0 = výchozí jednotka, 1 = A, 2 = B a tak dále).

Pokud zadaná jednotka není k dispozici nebo nelze určit druh jednotky (například vyměnitelné, pevné, CD-ROM, RAM disk nebo síťová jednotka), je vyvolána obslužná rutina neplatného parametru. Další informace naleznete v [tématu Ověření parametru](../../c-runtime-library/parameter-validation.md).

*Vyrovnávací paměti*<br/>
Umístění úložiště pro cestu nebo **NULL**.

Pokud je **zadána hodnota NULL,** tato funkce přiděluje vyrovnávací paměť alespoň *maximální* velikosti pomocí **malloc**a vrácená hodnota **_getdcwd** je ukazatel přidělené vyrovnávací paměti. Vyrovnávací paměť může být uvolněna voláním **free** a předáním ukazatele.

*mništinu*<br/>
Nenulové kladné celé číslo, které určuje maximální délku cesty, ve znacích: **char** pro **_getdcwd** a **wchar_t** pro **_wgetdcwd**.

Pokud *je plen* menší nebo rovno nule, je vyvolána obslužná rutina neplatného parametru. Další informace naleznete v [tématu Ověření parametru](../../c-runtime-library/parameter-validation.md).

## <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec, který představuje úplnou cestu aktuálního pracovního adresáře na zadané jednotce nebo **NULL**, což znamená chybu.

Pokud je *vyrovnávací paměť zadána* jako **NULL** a není dostatek paměti pro přidělení *maximálních* znaků, dojde k chybě a **errno** je nastavena na **ENOMEM**. Pokud délka cesty včetně ukončujícího znaku null přesáhne *množinu*, dojde k chybě a **hodnota errno** je nastavena na **hodnotu ERANGE**. Další informace o těchto kódech chyb naleznete [v tématech errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_getdcwd** získá úplnou cestu aktuálního pracovního adresáře na zadané jednotce a uloží jej do *vyrovnávací paměti*. Pokud je aktuální pracovní adresář nastaven na kořenový adresář,\\řetězec končí zpětným lomítkem ( ). Pokud je aktuální pracovní adresář nastaven na jiný adresář než kořenový adresář, řetězec končí názvem adresáře a nikoli zpětným lomítkem.

**_wgetdcwd** je širokoznaková verze **_getdcwd**a její parametr *vyrovnávací paměti* a vrácená hodnota jsou řetězce s širokými znaky. V opačném případě **se _wgetdcwd** a **_getdcwd** chovají stejně.

Tato funkce je bezpečná pro přístup z více vláken, i když závisí na **getfullpathname**, který sám o sobě není bezpečný pro přístup z více vláken. Však můžete porušit bezpečnost podprocesu, pokud vaše vícevláknové aplikace volá tuto funkci i [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew).

Verze této funkce, která má **_nolock** příponu se chová stejně k této funkci s tím rozdílem, že není bezpečná pro přístup z více vláken a není chráněna před rušením jinými vlákny. Další informace naleznete [v tématu _getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md).

Pokud jsou definovány **_DEBUG** a **_CRTDBG_MAP_ALLOC,** volání **_getdcwd** a **_wgetdcwd** jsou nahrazeny volání **mi _getdcwd_dbg** a **_wgetdcwd_dbg,** takže můžete ladit přidělení paměti. Další informace naleznete[v tématu _getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad v [_getdrive](getdrive.md).

## <a name="see-also"></a>Viz také

[Řízení adresářů](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
