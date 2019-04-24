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
ms.openlocfilehash: 464a254775d9a1d2488247d6dafb4b85cd763f10
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331828"
---
# <a name="getdcwd-wgetdcwd"></a>_getdcwd, _wgetdcwd

Získá celou cestu aktuálního pracovního adresáře na zadané jednotce.

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

Pokud zadaná jednotka není k dispozici, nebo druh jednotky (například vyměnitelný, pevný, CD-ROM, RAM disk nebo síťová jednotka) nelze určit, je vyvolána obslužná rutina neplatného parametru. Další informace najdete v tématu [Parameter Validation](../../c-runtime-library/parameter-validation.md).

*Vyrovnávací paměti*<br/>
Umístění úložiště pro cestu, nebo **NULL**.

Pokud **NULL** není zadána, tato funkce přidělí vyrovnávací paměť alespoň *maxlen* velikost pomocí **malloc**a návratová hodnota **_getdcwd –** je ukazatel do přidělené vyrovnávací paměti. Vyrovnávací paměť lze uvolnit voláním **bezplatné** a jeho předáním ukazateli.

*maxlen*<br/>
Nenulové kladné celé číslo, které určuje maximální délku cesty ve znacích: **char** pro **_getdcwd –** a **wchar_t** pro **_wgetdcwd –**.

Pokud *maxlen* je menší než nebo rovna hodnotě nula, je vyvolána obslužná rutina neplatného parametru. Další informace najdete v tématu [Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec, který představuje úplnou cestu aktuálního pracovního adresáře na zadané jednotce nebo **NULL**, což znamená chybu.

Pokud *vyrovnávací paměti* je zadán jako **NULL** a není dostatek paměti k přidělení *maxlen* znaky, dojde k chybě a **errno** je Nastavte na **ENOMEM**. Pokud délka cesty, včetně ukončujícího znaku null překročí *maxlen*, dojde k chybě, a **errno** je nastavena na **ERANGE**. Další informace o těchto chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Getdcwd –** funkce získá celou cestu aktuálního pracovního adresáře na zadané jednotce a ukládá ji do *vyrovnávací paměti*. Pokud je aktuální pracovní adresář nastaven na kořen, řetězec končí zpětným lomítkem (\\). Pokud aktuální pracovní adresář nastaven na jiný adresář než kořenový, řetězec skončí názvem adresáře, nikoli zpětným lomítkem.

**_wgetdcwd –** je verze širokého znaku **_getdcwd –** a jeho *vyrovnávací paměti* parametr a návratová hodnota jsou širokoznaké řetězce. V opačném případě **_wgetdcwd –** a **_getdcwd –** chovají identicky.

Tato funkce je bezpečná pro vlákno, přestože je závislá na **GetFullPathName**, což je samotný není bezpečná pro vlákno. Však můžete porušit bezpečnost vlákna, pokud vaše aplikace s více vlákny volá tuto funkci a [GetFullPathNameA](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).

Verze této funkce, která má **_nolock** přípona chová stejně jako na tuto funkci s tím rozdílem, že není bezpečné pro vlákna a není chráněna před rušením jinými vlákny. Další informace najdete v tématu [_getdcwd_nolock – _wgetdcwd_nolock –](getdcwd-nolock-wgetdcwd-nolock.md).

Když **_DEBUG** a **_CRTDBG_MAP_ALLOC** jsou definovány, volání **_getdcwd –** a **_wgetdcwd –** jsou nahrazena voláními **_getdcwd_dbg –** a **_wgetdcwd_dbg –** tak, aby můžete ladit přidělování paměti. Další informace najdete v tématu[_getdcwd_dbg – _wgetdcwd_dbg –](getdcwd-dbg-wgetdcwd-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<Direct.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_getdrive –](getdrive.md).

## <a name="see-also"></a>Viz také:

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
