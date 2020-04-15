---
title: _splitpath_s, _wsplitpath_s
ms.date: 4/2/2020
api_name:
- _wsplitpath_s
- _splitpath_s
- _o__splitpath_s
- _o__wsplitpath_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 364544a9423668494747405e801d59b73de4e6c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355623"
---
# <a name="_splitpath_s-_wsplitpath_s"></a>_splitpath_s, _wsplitpath_s

Rozdělí název cesty na součásti. Jedná se o verze [_splitpath, _wsplitpath](splitpath-wsplitpath.md) s vylepšeními zabezpečení popsanými v [části Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

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

*Cestu*<br/>
Úplná cesta.

*Jednotky*<br/>
Písmeno jednotky následované dvojtečkou (**:**). Pokud nepotřebujete písmeno jednotky, můžete pro tento parametr předat **hodnotu NULL.**

*driveNumberOfElements*<br/>
Velikost vyrovnávací paměti *jednotky* v jednobajtové nebo široké znaky. Pokud je *jednotka* **null**, musí být tato hodnota 0.

*Dir*<br/>
Cesta adresáře, včetně koncového lomítka. Lze použít **/** lomítka **\\** ( ), zpětná lomítka ( ) nebo obojí. Pokud nepotřebujete cestu k adresáři, můžete pro tento parametr předat **hodnotu NULL.**

*dirNumberOfElements*<br/>
Velikost *dir* vyrovnávací paměti v jednobajtové nebo široké znaky. Pokud *dir* je **NULL**, tato hodnota musí být 0.

*Fname*<br/>
Základní název souboru (bez přípony). Pokud název souboru nepotřebujete, můžete pro tento parametr předat hodnotu **NULL.**

*názevNumberOfElements*<br/>
Velikost vyrovnávací paměti *fname* v jednobajtové nebo široké znaky. Pokud je hodnota **null** *,* musí být tato hodnota 0.

*Ext*<br/>
Přípona názvu souboru, včetně úvodního období (**.**). Pokud příponu název souboru nepotřebujete, můžete pro tento parametr předat **hodnotu NULL.**

*extNumberOfElements*<br/>
Velikost vyrovnávací paměti *ext* v jednobajtových nebo širokých znacích. Pokud *ext* je **NULL**, tato hodnota musí být 0.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; kód chyby při selhání.

### <a name="error-conditions"></a>Chybové stavy

|Podmínka|Návratová hodnota|
|---------------|------------------|
|*cesta* je **NULL**|**EINVAL**|
|*jednotka* je **null**, *driveNumberOfElements* je nenulová|**EINVAL**|
|*jednotka* není**null**, *driveNumberOfElements* je nula|**EINVAL**|
|*dir* je **NULL**, *dirNumberOfElements* je nenulová|**EINVAL**|
|*dir* není**null**, *dirNumberOfElements* je nula|**EINVAL**|
|*fname* je **NULL**, *nameNumberOfElements* je nenulová|**EINVAL**|
|*fname* není**null**, *nameNumberOfElements* je nula|**EINVAL**|
|*ext* je **NULL**, *extNumberOfElements* je nenulová|**EINVAL**|
|*ext* není**null**, *extNumberOfElements* je nula|**EINVAL**|

Pokud dojde k některé z výše uvedených podmínek, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md) . Pokud je spuštění povoleno pokračovat, tyto funkce nastavit **errno** na **EINVAL** a vrátit **EINVAL**.

Pokud je některá z vyrovnávacích pamětí příliš krátká pro uložení výsledku, tyto funkce vymažou všechny vyrovnávací paměti na prázdné řetězce, nastaví **chybní stav** na **ERANGE**a vrátí **ERANGE**.

## <a name="remarks"></a>Poznámky

Funkce **_splitpath_s** rozdělí cestu na čtyři součásti. **_splitpath_s** podle potřeby automaticky zpracovává argumenty vícebajtových řetězců a rozpozná se sekvence vícebajtových znaků podle aktuálně používáné vícebajtové znakové stránky. **_wsplitpath_s** je širokoznaková verze **_splitpath_s**; argumenty, které **mají _wsplitpath_s,** jsou řetězce s širokými znaky. Tyto funkce se chovají stejně jinak

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Každá součást úplné cesty je uložena v samostatné vyrovnávací paměti; konstanty manifestu **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**a **_MAX_EXT** (definované v STDLIB. H) určete maximální přípustnou velikost pro každou součást souboru. Součásti souboru větší než odpovídající konstanty manifestu způsobují poškození haldy.

V následující tabulce jsou uvedeny hodnoty konstant manifestu.

|Name (Název)|Hodnota|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Pokud úplná cesta neobsahuje komponentu (například název souboru), **_splitpath_s** přiřadí odpovídající vyrovnávací paměti prázdný řetězec.

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky, což eliminuje potřebu zadat argument velikosti. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze knihovny těchto funkcí nejprve vyplní vyrovnávací paměť 0xFE. Chcete-li toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_splitpath_s**|\<stdlib.h>|
|**_wsplitpath_s**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
