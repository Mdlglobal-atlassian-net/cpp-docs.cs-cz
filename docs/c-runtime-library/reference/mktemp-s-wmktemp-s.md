---
title: _mktemp_s, _wmktemp_s
ms.date: 4/2/2020
api_name:
- _mktemp_s
- _wmktemp_s
- _o__mktemp_s
- _o__wmktemp_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
helpviewer_keywords:
- _tmktemp_s function
- mktemp_s function
- _wmktemp_s function
- _mktemp_s function
- files [C++], temporary
- tmktemp_s function
- wmktemp_s function
- temporary files [C++]
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
ms.openlocfilehash: 061c5647b2c5a5e79b017cf93989f62ad19cfc0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338755"
---
# <a name="_mktemp_s-_wmktemp_s"></a>_mktemp_s, _wmktemp_s

Vytvoří jedinečný název souboru. Jedná se o verze [_mktemp, _wmktemp](mktemp-wmktemp.md) s vylepšeními zabezpečení popsanými v [části Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _mktemp_s(
   char *nameTemplate,
   size_t sizeInChars
);
errno_t _wmktemp_s(
   wchar_t *nameTemplate,
   size_t sizeInChars
);
template <size_t size>
errno_t _mktemp_s(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
errno_t _wmktemp_s(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*názevŠablona*<br/>
Vzor názvu souboru.

*sizeInChars*<br/>
Velikost vyrovnávací paměti v jednobajtových znacích v **_mktemp_s**; široké znaky v **_wmktemp_s**, včetně zakončení null.

## <a name="return-value"></a>Návratová hodnota

Obě tyto funkce vrátí nulu na úspěch; kód chyby při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*názevŠablona*|*sizeInChars*|Návratová hodnota|Nová hodnota v *nameTemplate*|
|----------------|-------------------|----------------------|-------------------------------|
|**Null**|jakékoli|**EINVAL**|**Null**|
|Nesprávný formát (správný formát naleznete v části Poznámky)|jakékoli|**EINVAL**|prázdný řetězec|
|jakékoli|<= počet X|**EINVAL**|prázdný řetězec|

Pokud dojde k některéz výše uvedených chybových stavů, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_mktemp_s** vytvoří jedinečný název souboru změnou argumentu *nameTemplate,* takže po volání ukazatel *nameTemplate* odkazuje na řetězec obsahující nový název souboru. **_mktemp_s** podle potřeby automaticky zpracovává argumenty vícebajtových řetězců a rozpozná se sekvence vícebajtových znaků podle vícebajtové znakové stránky, kterou systém run-time aktuálně používá. **_wmktemp_s** je širokoznaková verze **_mktemp_s**; argument **_wmktemp_s** je řetězec s širokým znakem. **_wmktemp_s** a **_mktemp_s** se chovají stejně jinak, s tím rozdílem, že **_wmktemp_s** nezpracovává vícebajtové řetězce znaků.

Ladicí verze knihovny těchto funkcí nejprve vyplní vyrovnávací paměť 0xFE. Chcete-li toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

Argument *nameTemplate* má formulář **baseXXXXXX**, kde *base* je část nového názvu souboru, kterou zadáte, a každý X je zástupný symbol pro znak dodaný **_mktemp_s**. Každý zástupný znak v *názvuŠablona* musí být velké X. **_mktemp_s** zachová *základnu* a nahradí první koncové X abecedním znakem. **_mktemp_s** nahradí následující koncové X pětimístnou hodnotou; Tato hodnota je jedinečné číslo identifikující volající proces nebo v vícevláknových programech volající vlákno.

Každé úspěšné volání **_mktemp_s** upravuje *nameTemplate*. Při každém následném volání ze stejného procesu nebo vlákna se stejným *názvemTemplate* **argument, _mktemp_s** kontroluje názvy souborů, které odpovídají názvy vrácené **_mktemp_s** v předchozích voláních. Pokud pro daný název neexistuje žádný soubor, **vrátí _mktemp_s** tento název. Pokud existují soubory pro všechny dříve vrácené názvy, **_mktemp_s** vytvoří nový název nahrazením abecedního znaku, který použil v dříve vráceném názvu, dalším dostupným písmenem s malou písmeno v pořadí od "a" do "z". Například pokud *je základna:*

> **Fn**

a pětimístná hodnota dodaná **společností _mktemp_s** je 12345, první vrácené jméno je:

> **fna12345**

Pokud tento název se používá k vytvoření souboru FNA12345 a tento soubor stále existuje, další název vrácený při volání ze stejného procesu nebo vlákna se stejným *základem* pro *nameTemplate* je:

> **fnb12345**

Pokud FNA12345 neexistuje, další vrácený název je znovu:

> **fna12345**

**_mktemp_s** můžete vytvořit maximálně 26 jedinečných názvů souborů pro libovolnou kombinaci *základních* a *nameTemplate* hodnot. FnZ12345 je tedy poslední jedinečný název **souboru, _mktemp_s** můžete vytvořit pro *základní* a *nameTemplate* hodnoty použité v tomto příkladu.

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky (eliminuje potřebu zadat argument velikosti) a mohou automaticky nahradit starší, nezabezpečené funkce s jejich novější, bezpečné protějšky. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mktemp_s**|\<io.h>|
|**_wmktemp_s**|\<io.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```cpp
// crt_mktemp_s.cpp
/* The program uses _mktemp to create
* five unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>

char *fnTemplate = "fnXXXXXX";
char names[5][9];

int main()
{
   int i, err, sizeInChars;
   FILE *fp;

   for( i = 0; i < 5; i++ )
   {
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );
      /* Get the size of the string and add one for the null terminator.*/
      sizeInChars = strnlen(names[i], 9) + 1;
      /* Attempt to find a unique filename: */
      err = _mktemp_s( names[i], sizeInChars );
      if( err != 0 )
         printf( "Problem creating the template" );
      else
      {
         if( fopen_s( &fp, names[i], "w" ) == 0 )
            printf( "Unique filename is %s\n", names[i] );
         else
            printf( "Cannot open %s\n", names[i] );
         fclose( fp );
      }
   }

   return 0;
}
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Unique filename is fna03188
Unique filename is fnb03188
Unique filename is fnc03188
Unique filename is fnd03188
Unique filename is fne03188
```

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
