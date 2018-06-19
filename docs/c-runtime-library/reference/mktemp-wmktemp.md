---
title: _mktemp –, _wmktemp – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 087348b3cc59fb1b47699fc0e64f533c22d992b4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404344"
---
# <a name="mktemp-wmktemp"></a>_mktemp, _wmktemp

Vytvoří jedinečný název souboru. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_mktemp_s –, _wmktemp_s –](mktemp-s-wmktemp-s.md).

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

Každá z těchto funkcí upravené nameTemplate vrátí ukazatel. Funkce vrátí hodnotu **NULL** Pokud *nameTemplate* je chybně vytvořen nebo z daného nameTemplate možné vytvářet žádné další jedinečné názvy.

## <a name="remarks"></a>Poznámky

**_Mktemp –** funkce vytvoří jedinečný název souboru změnou *nameTemplate* argument. **_mktemp –** automaticky zpracovává argumenty řetězce vícebajtových znaků podle potřeby, rozpozná sekvencí vícebajtových znaků podle vícebajtové znakové stránky aktuálně používána v běhu systému. **_wmktemp –** je verze široká charakterová **_mktemp –**; argument a vrátí hodnotu **_wmktemp –** jsou široká charakterová řetězce. **_wmktemp –** a **_mktemp –** chovat jinak, stejně jako vyjma toho, že **_wmktemp –** nezpracovává řetězců vícebajtových znaků.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp –**|**_mktemp**|**_mktemp**|**_wmktemp**|

*NameTemplate* argument má formulář *základní ** XXXXXX*, kde *základní* je součástí nový název souboru, který zadáte a každá X je zástupný symbol pro znak poskytl **_mktemp –**. Každý zástupný znak v *nameTemplate* musí být velká X. **_mktemp –** zachovává *základní* a nahradí první Koncové X znakem abecedy. **_mktemp –** nahrazuje následující koncové značkou s hodnotou pět číslic; tato hodnota je jedinečné číslo identifikující volání zpracovat, nebo programy s více vlákny, volající vlákno.

Každé úspěšné volání **_mktemp –** upraví *nameTemplate*. Při každém následných volání z stejný postup nebo vlákno se stejným *nameTemplate* argument, **_mktemp –** kontroly pro názvy souborů, které odpovídají názvy vrácené **_mktemp –** v předchozí volání. Pokud pro daného názvu, neexistuje žádný soubor **_mktemp –** vrátí tímto názvem. Pokud soubory existují pro všechny názvy, předtím vrátila **_mktemp –** vytvoří nový název nahrazením znak abecedy použije v názvu dříve vrácený s další dostupné malé písmeno, v pořadí od 'a' do 'z'. Například pokud *základní* je:

> **fn**

a hodnotu pět číslic poskytl **_mktemp –** 12345, je vrácena křestní jméno:

> **fna12345**

Pokud tento název se používá k vytvoření souboru FNA12345 a tento soubor stále existuje, další název vrátila volání ze stejné procesu nebo vlákno se stejným *základní* pro *nameTemplate* je:

> **fnb12345**

Pokud FNA12345 neexistuje, je další název vrácený znovu:

> **fna12345**

**_mktemp –** můžete vytvořit maximálně 26 jedinečných názvů souborů pro libovolnou kombinaci daného *základní* a *nameTemplate* hodnoty. Proto je FNZ12345 příjmení jedinečný soubor **_mktemp –** můžete vytvořit pro *základní* a *nameTemplate* hodnoty používané v tomto příkladu.

Při selhání **errno** nastavena. Pokud *nameTemplate* má neplatný formát (například méně než 6 značkou), **errno** je nastaven na **einval –**. Pokud **_mktemp –** se nepodařilo vytvořit jedinečný název, protože názvy všech 26 možné soubor již existuje, **_mktemp –** nastaví nameTemplate na prázdný řetězec a vrátí **eexist –**.

V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mktemp**|\<IO.h >|
|**_wmktemp**|\<IO.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile](tmpfile.md)<br/>
