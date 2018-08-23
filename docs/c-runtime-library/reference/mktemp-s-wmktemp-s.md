---
title: _mktemp_s – _wmktemp_s – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mktemp_s
- _wmktemp_s
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
apitype: DLLExport
f1_keywords:
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb4fcd681cc5286d02f0a7b8cb4ff95b8f3dd911
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42464807"
---
# <a name="mktemps-wmktemps"></a>_mktemp_s, _wmktemp_s

Vytvoří jedinečný název souboru. Jde o verzích [_mktemp – _wmktemp –](mktemp-wmktemp.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*nameTemplate*<br/>
Vzor názvů souborů.

*sizeInChars*<br/>
Velikost vyrovnávací paměti v jednobajtové znaky v **_mktemp_s –**; široké znaky v **_wmktemp_s –**, včetně ukončovacího znaku null.

## <a name="return-value"></a>Návratová hodnota

Obě tyto funkce vrací nulu v případě úspěchu; Kód chyby při selhání.

### <a name="error-conditions"></a>Chybové podmínky

|*nameTemplate*|*sizeInChars*|Návratová hodnota|Nová hodnota v *nameTemplate*|
|----------------|-------------------|----------------------|-------------------------------|
|**HODNOTU NULL**|Všechny|**EINVAL**|**HODNOTU NULL**|
|Nesprávný formát (viz poznámky části správný formát)|Všechny|**EINVAL**|Prázdný řetězec|
|Všechny|< = počet bezpodmínečný|**EINVAL**|Prázdný řetězec|

Pokud dojde k některé z výše uvedených chybové stavy, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

**_Mktemp_s –** funkce vytvoří jedinečný název souboru tak, že upravíte *nameTemplate* argument, tak, aby po volání, *nameTemplate* ukazatel odkazuje na řetězec nový název souboru obsahujícího. **_mktemp_s –** automaticky zpracovává argumenty vícebajtových řetězců znaků podle potřeby, rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která aktuálně používaných systémem za běhu. **_wmktemp_s –** je verze širokého znaku **_mktemp_s –**; argument **_wmktemp_s –** je širokoznaký řetězec. **_wmktemp_s –** a **_mktemp_s –** se jinak chovají stejně, s výjimkou, že **_wmktemp_s –** nezpracovává vícebajtové znakové řetězce.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s –**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

*NameTemplate* argument má tvar **baseXXXXXX**, kde *základní* je součástí nový název souboru, který zadáte, a každá X je zástupný symbol pro znak poskytl **_mktemp_s –**. Každý zástupný znak v *nameTemplate* musí být velké písmeno x **_mktemp_s –** zachová *základní* a nahradí první Koncové X abecední znak. **_mktemp_s –** nahrazuje následující koncové bezpodmínečný s hodnotou pět číslic; tato hodnota je jedinečné číslo identifikující volání procesu, nebo v programech s více vlákny, volajícího vlákna.

Každé úspěšné volání **_mktemp_s –** upraví *nameTemplate*. V každé následné volání ze stejného procesu nebo vlákna se stejným *nameTemplate* argument, **_mktemp_s –** kontroluje názvy souborů, které odpovídají názvům vrácený **_mktemp_s –** v předchozích volání. Pokud neexistuje žádný soubor pro daný název **_mktemp_s –** vrátí tento název. Pokud soubor existuje pro všechny názvy, dříve vrácené **_mktemp_s –** vytvoří nový název nahrazením abecední znak použít v názvu dříve vrácenou s další dostupné malé písmeno, v pořadí od "a" až "z". Například pokud *základní* je:

> **fn**

a hodnota pět číslic poskytnutých **_mktemp_s –** 12345, je vrácena křestní jméno:

> **fna12345**

Pokud tento název se používá k vytvoření souboru FNA12345 a tento soubor stále existuje, další název vrátil volání od stejného procesu nebo vlákna se stejným *základní* pro *nameTemplate* je:

> **fnb12345**

Pokud FNA12345 neexistuje, další název vrácený opět:

> **fna12345**

**_mktemp_s –** můžete vytvořit až 26 jedinečné názvy souborů pro libovolnou kombinaci dané *základní* a *nameTemplate* hodnoty. Proto FNZ12345 je poslední jedinečný název **_mktemp_s –** můžete vytvořit *základní* a *nameTemplate* hodnot použitých v tomto příkladu.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (tím eliminuje nutnost zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mktemp_s**|\<IO.h >|
|**_wmktemp_s**|\<IO.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
