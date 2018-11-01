---
title: _splitpath_s, _wsplitpath_s
ms.date: 11/04/2016
apiname:
- _wsplitpath_s
- _splitpath_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 5a6770b7f5f0f8ee82cf86757d14e03b33c1f5d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602901"
---
# <a name="splitpaths-wsplitpaths"></a>_splitpath_s, _wsplitpath_s

Název cesty rozdělí do komponenty. Jde o verzích [_splitpath – _wsplitpath –](splitpath-wsplitpath.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Úplná cesta.

*Jednotky*<br/>
Písmeno, za nímž následuje dvojtečka (**:**). Můžete předat **NULL** pro tento parametr, pokud není nutné písmeno jednotky.

*driveNumberOfElements*<br/>
Velikost *jednotky* vyrovnávací paměti ve znacích jednobajtové nebo široké. Pokud *jednotky* je **NULL**, tato hodnota musí být 0.

*adresář*<br/>
Cesta k adresáři, včetně koncového lomítka. Lomítka ( **/** ), zpětná lomítka ( **\\** ), nebo obě mohou být použity. Můžete předat **NULL** pro tento parametr, pokud není nutné cesta k adresáři.

*dirNumberOfElements*<br/>
Velikost *dir* vyrovnávací paměti ve znacích jednobajtové nebo široké. Pokud *dir* je **NULL**, tato hodnota musí být 0.

*%{fname/*<br/>
Základní název souboru (bez přípony). Můžete předat **NULL** pro tento parametr, pokud není nutné název souboru.

*nameNumberOfElements*<br/>
Velikost *%{fname/* vyrovnávací paměti ve znacích jednobajtové nebo široké. Pokud *%{fname/* je **NULL**, tato hodnota musí být 0.

*ext, přípona*<br/>
Příponu názvu souboru, včetně počáteční období (**.**). Můžete předat **NULL** pro tento parametr, pokud není nutné příponu názvu souboru.

*extNumberOfElements*<br/>
Velikost *ext* vyrovnávací paměti ve znacích jednobajtové nebo široké. Pokud *ext* je **NULL**, tato hodnota musí být 0.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; Kód chyby při selhání.

### <a name="error-conditions"></a>Chybové podmínky

|Podmínka|Návratová hodnota|
|---------------|------------------|
|*cesta* je **NULL**|**EINVAL**|
|*jednotky* je **NULL**, *driveNumberOfElements* je nulová|**EINVAL**|
|*jednotky* jinou hodnotu než**NULL**, *driveNumberOfElements* je nula|**EINVAL**|
|*příkaz dir* je **NULL**, *dirNumberOfElements* je nulová|**EINVAL**|
|*příkaz dir* jinou hodnotu než**NULL**, *dirNumberOfElements* je nula|**EINVAL**|
|*%{fname/* je **NULL**, *nameNumberOfElements* je nulová|**EINVAL**|
|*%{fname/* jinou hodnotu než**NULL**, *nameNumberOfElements* je nula|**EINVAL**|
|*ext* je **NULL**, *extNumberOfElements* je nulová|**EINVAL**|
|*ext* jinou hodnotu než**NULL**, *extNumberOfElements* je nula|**EINVAL**|

Pokud dojde k některé z výše uvedených podmínek, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátit **EINVAL**.

Pokud některý z vyrovnávací paměti je příliš krátká pro uchování výsledku, tyto funkce, zrušte zaškrtnutí políčka vyrovnávací paměti na prázdné řetězce, nastavte **errno** k **ERANGE**a vrátí **ERANGE**.

## <a name="remarks"></a>Poznámky

**_Splitpath_s –** funkce rozdělí cestu do jeho čtyři součásti. **_splitpath_s –** automaticky zpracovává argumenty vícebajtových řetězců znaků podle potřeby, rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která aktuálně používán. **_wsplitpath_s –** je verze širokého znaku **_splitpath_s –**; argumenty, které mají **_wsplitpath_s –** jsou širokoznaké řetězce. Tyto funkce chovají identicky jinak

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Jednotlivé komponenty úplná cesta je uložena v samostatných vyrovnávací paměti; konstanty manifestu **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**, a **_MAX_EXT** (definované v STDLIB. H) zadejte maximální povolenou velikost pro každou komponentu souboru. Komponenty soubory větší než odpovídající konstant manifestu způsobit poškození haldy.

V následující tabulce jsou uvedeny hodnoty konstant manifestu.

|Název|Hodnota|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Pokud je úplná cesta neobsahuje součásti (například název_souboru), **_splitpath_s –** přiřadí prázdný řetězec odpovídající vyrovnávací paměti.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky, takže odpadá nutnost určit velikost argumentu. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze těchto funkcí nejprve naplní vyrovnávací paměť hodnotou 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_splitpath_s**|\<stdlib.h>|
|**_wsplitpath_s**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_makepath_s – _wmakepath_s –](makepath-s-wmakepath-s.md).

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
