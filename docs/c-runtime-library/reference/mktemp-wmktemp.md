---
title: _mktemp, _wmktemp
ms.date: 11/04/2016
apiname:
- _wmktemp
- _mktemp
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
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
helpviewer_keywords:
- _wmktemp function
- _mktemp function
- files [C++], temporary
- tmktemp function
- _tmktemp function
- wmktemp function
- mktemp function
- temporary files [C++]
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
ms.openlocfilehash: c1c5f0ee12c9e07d76405014bb4a6a6ecc7d97e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156509"
---
# <a name="mktemp-wmktemp"></a>_mktemp, _wmktemp

Vytvoří jedinečný název souboru. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [_mktemp_s – _wmktemp_s –](mktemp-s-wmktemp-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_mktemp(
   char *nameTemplate
);
wchar_t *_wmktemp(
   wchar_t *nameTemplate
);
template <size_t size>
char *_mktemp(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
wchar_t *_wmktemp(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*nameTemplate*<br/>
Vzor názvů souborů.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na upravený nameTemplate. Funkce vrátí **NULL** Pokud *nameTemplate* je chybně vytvořený kód nebo z daného nameTemplate možné vytvářet žádné další jedinečné názvy.

## <a name="remarks"></a>Poznámky

**_Mktemp –** funkce vytvoří jedinečný název souboru tak, že upravíte *nameTemplate* argument. **_mktemp –** automaticky zpracovává argumenty vícebajtových řetězců znaků podle potřeby, rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která aktuálně používaných systémem za běhu. **_wmktemp –** je verze širokého znaku **_mktemp –**; argument a návratová hodnota funkce **_wmktemp –** jsou širokoznaké řetězce. **_wmktemp –** a **_mktemp –** se jinak chovají stejně, s výjimkou, že **_wmktemp –** nezpracovává vícebajtové znakové řetězce.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

*NameTemplate* argument má tvar *základní*XXXXXX, kde *základní* je součástí nový název souboru, který zadáte, a každá X je zástupný symbol pro znak poskytl **_mktemp –**. Každý zástupný znak v *nameTemplate* musí být velké písmeno x **_mktemp –** zachová *základní* a nahradí první Koncové X abecední znak. **_mktemp –** nahrazuje následující koncové bezpodmínečný s hodnotou pět číslic; tato hodnota je jedinečné číslo identifikující volání procesu, nebo v programech s více vlákny, volajícího vlákna.

Každé úspěšné volání **_mktemp –** upraví *nameTemplate*. V každé následné volání ze stejného procesu nebo vlákna se stejným *nameTemplate* argument, **_mktemp –** kontroluje názvy souborů, které odpovídají názvům vrácený **_mktemp –** v předchozí volání. Pokud neexistuje žádný soubor pro daný název **_mktemp –** vrátí tento název. Pokud soubor existuje pro všechny názvy, dříve vrácené **_mktemp –** vytvoří nový název nahrazením abecední znak použít v názvu dříve vrácenou s další dostupné malé písmeno, v pořadí od "a" až "z". Například pokud *základní* je:

> **fn**

a hodnota pět číslic poskytnutých **_mktemp –** 12345, je vrácena křestní jméno:

> **fna12345**

Pokud tento název se používá k vytvoření souboru FNA12345 a tento soubor stále existuje, další název vrátil volání od stejného procesu nebo vlákna se stejným *základní* pro *nameTemplate* je:

> **fnb12345**

Pokud FNA12345 neexistuje, další název vrácený opět:

> **fna12345**

**_mktemp –** můžete vytvořit až 26 jedinečné názvy souborů pro libovolnou kombinaci dané *základní* a *nameTemplate* hodnoty. Proto FNZ12345 je poslední jedinečný název **_mktemp –** můžete vytvořit *základní* a *nameTemplate* hodnot použitých v tomto příkladu.

Při selhání **errno** nastavena. Pokud *nameTemplate* má neplatný formát (třeba méně než 6 bezpodmínečný), **errno** je nastavena na **EINVAL**. Pokud **_mktemp –** nemůže vytvořit jedinečný název, protože názvy všech 26 možné soubor ještě neexistuje, **_mktemp –** nastaví nameTemplate na prázdný řetězec a vrátí **EEXIST**.

V jazyce C++ mají tyto funkce přetížení šablon, která vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<IO.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_mktemp.c
// compile with: /W3
/* The program uses _mktemp to create
* unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>
#include <errno.h>

char *template = "fnXXXXXX";
char *result;
char names[27][9];

int main( void )
{
   int i;
   FILE *fp;

   for( i = 0; i < 27; i++ )
   {
      strcpy_s( names[i], sizeof( names[i] ), template );
      /* Attempt to find a unique filename: */
      result = _mktemp( names[i] );  // C4996
      // Note: _mktemp is deprecated; consider using _mktemp_s instead
      if( result == NULL )
      {
         printf( "Problem creating the template\n" );
         if (errno == EINVAL)
         {
             printf( "Bad parameter\n");
         }
         else if (errno == EEXIST)
         {
             printf( "Out of unique filenames\n");
         }
      }
      else
      {
         fopen_s( &fp, result, "w" );
         if( fp != NULL )
            printf( "Unique filename is %s\n", result );
         else
            printf( "Cannot open %s\n", result );
         fclose( fp );
      }
   }
}
```

```Output
Unique filename is fna03912
Unique filename is fnb03912
Unique filename is fnc03912
Unique filename is fnd03912
Unique filename is fne03912
Unique filename is fnf03912
Unique filename is fng03912
Unique filename is fnh03912
Unique filename is fni03912
Unique filename is fnj03912
Unique filename is fnk03912
Unique filename is fnl03912
Unique filename is fnm03912
Unique filename is fnn03912
Unique filename is fno03912
Unique filename is fnp03912
Unique filename is fnq03912
Unique filename is fnr03912
Unique filename is fns03912
Unique filename is fnt03912
Unique filename is fnu03912
Unique filename is fnv03912
Unique filename is fnw03912
Unique filename is fnx03912
Unique filename is fny03912
Unique filename is fnz03912
Problem creating the template.
Out of unique filenames.
```

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile](tmpfile.md)<br/>
