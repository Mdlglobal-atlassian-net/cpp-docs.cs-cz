---
title: _splitpath_s, _wsplitpath_s
ms.date: 11/04/2016
api_name:
- _wsplitpath_s
- _splitpath_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
ms.openlocfilehash: f97c07ed01ae629fe3eb61346c6c0fcd8fa803f0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958056"
---
# <a name="_splitpath_s-_wsplitpath_s"></a>_splitpath_s, _wsplitpath_s

Přeruší název cesty na součásti. Jedná se o verze [_splitpath, _wsplitpath](splitpath-wsplitpath.md) s vylepšeními zabezpečení, jak [je popsáno v části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _splitpath_s(
   const char * path,
   char * drive,
   size_t driveNumberOfElements,
   char * dir,
   size_t dirNumberOfElements,
   char * fname,
   size_t nameNumberOfElements,
   char * ext,
   size_t extNumberOfElements
);
errno_t _wsplitpath_s(
   const wchar_t * path,
   wchar_t * drive,
   size_t driveNumberOfElements,
   wchar_t *dir,
   size_t dirNumberOfElements,
   wchar_t * fname,
   size_t nameNumberOfElements,
   wchar_t * ext,
   size_t extNumberOfElements
);
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _splitpath_s(
   const char *path,
   char (&drive)[drivesize],
   char (&dir)[dirsize],
   char (&fname)[fnamesize],
   char (&ext)[extsize]
); // C++ only
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _wsplitpath_s(
   const wchar_t *path,
   wchar_t (&drive)[drivesize],
   wchar_t (&dir)[dirsize],
   wchar_t (&fname)[fnamesize],
   wchar_t (&ext)[extsize]
); // C++ only
```

### <a name="parameters"></a>Parametry

*Cesta*<br/>
Úplná cesta

*drive*<br/>
Písmeno jednotky následovaný dvojtečkou ( **:** ). Pokud nepotřebujete písmeno jednotky, můžete pro tento parametr předat **hodnotu null** .

*driveNumberOfElements*<br/>
Velikost vyrovnávací paměti *jednotky* v jednobajtových nebo velkých znacích. Pokud má jednotka **hodnotu null**, tato hodnota musí být 0.

*dir*<br/>
Cesta k adresáři, včetně koncového lomítka. Lze použít lomítka **/** (), zpětná lomítka ( **\\** ) nebo obojí. Pokud nepotřebujete cestu k adresáři, můžete pro tento parametr předat **hodnotu null** .

*dirNumberOfElements*<br/>
Velikost vyrovnávací paměti *adresáře* v jednobajtových nebo velkých znacích. Pokud má dir **hodnotu null**, tato hodnota musí být 0.

*fname*<br/>
Základní název souboru (bez přípony) Pokud název souboru nepotřebujete, můžete pro tento parametr předat **hodnotu null** .

*nameNumberOfElements*<br/>
Velikost vyrovnávací paměti *fname* v jednobajtových nebo velkých znacích. Pokud má fname **hodnotu null**, tato hodnota musí být 0.

*ext*<br/>
Přípona názvu souboru včetně úvodní tečky ( **.** ) Pokud nepotřebujete příponu filename, můžete pro tento parametr předat **hodnotu null** .

*extNumberOfElements*<br/>
Velikost *Rozšířené* vyrovnávací paměti v jednobajtových nebo velkých znacích. Pokud má EXT **hodnotu null**, tato hodnota musí být 0.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; chybový kód při selhání.

### <a name="error-conditions"></a>Chybové stavy

|Podmínka|Návratová hodnota|
|---------------|------------------|
|*cesta* má **hodnotu null** .|**EINVAL**|
|*jednotka* má **hodnotu null**, *driveNumberOfElements* je nenulová.|**EINVAL**|
|*jednotka* je**nenulová**, *driveNumberOfElements* je nula.|**EINVAL**|
|*dir* má **hodnotu null**, *dirNumberOfElements* je nenulový.|**EINVAL**|
|*dir* má jinou**hodnotu než null**, *dirNumberOfElements* je nula.|**EINVAL**|
|*fname* má **hodnotu null**, *nameNumberOfElements* není nula.|**EINVAL**|
|*fname* je**null**, *nameNumberOfElements* je nula.|**EINVAL**|
|Hodnota *EXT* má **hodnotu null**, *extNumberOfElements* je nenulová.|**EINVAL**|
|hodnota *EXT* je jiná než**null**, *extNumberOfElements* je nula.|**EINVAL**|

Pokud nastane kterákoli z výše uvedených podmínek, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

Pokud je některá z vyrovnávacích pamětí příliš krátká pro výsledek, tyto funkce vymažou všechny vyrovnávací paměti do prázdných řetězců, nastaví **errno** na **ERANGE**a vrátí **ERANGE**.

## <a name="remarks"></a>Poznámky

Funkce **_splitpath_s** přerušuje cestu na čtyři součásti. **_splitpath_s** automaticky zpracovává argumenty vícebajtového řetězce znaků podle potřeby a rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která se právě používá. **_wsplitpath_s** je **_splitpath_s**verze s velkým znakem; argumenty **_wsplitpath_s** jsou řetězce s libovolným znakem. Tyto funkce se chovají identicky jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Každá součást úplné cesty je uložena v samostatné vyrovnávací paměti; v manifestu jsou konstanty **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**a **_MAX_EXT** (definované v Stdlib. H) zadejte maximální povolenou velikost pro jednotlivé součásti souborů. Součásti souboru větší než odpovídající konstanty manifestu způsobují poškození haldy.

V následující tabulce jsou uvedeny hodnoty konstant manifestu.

|Name|Value|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Pokud úplná cesta neobsahuje komponentu (například filename), **_splitpath_s** přiřadí do odpovídající vyrovnávací paměti prázdný řetězec.

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky a eliminují nutnost zadat argument Size. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze těchto funkcí nejprve naplní vyrovnávací paměť pomocí 0xFD. Pokud chcete toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_splitpath_s**|\<stdlib.h>|
|**_wsplitpath_s**|\<Stdlib. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
