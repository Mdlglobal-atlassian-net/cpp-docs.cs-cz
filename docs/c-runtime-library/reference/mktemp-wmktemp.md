---
title: _mktemp, _wmktemp
ms.date: 4/2/2020
api_name:
- _wmktemp
- _mktemp
- _o__mktemp
- _o__wmktemp
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
ms.openlocfilehash: 8affd20ca7826f0d383f749567c9625d61dacd48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338719"
---
# <a name="_mktemp-_wmktemp"></a>_mktemp, _wmktemp

Vytvoří jedinečný název souboru. K dispozici jsou bezpečnější verze těchto funkcí. viz [_mktemp_s, _wmktemp_s](mktemp-s-wmktemp-s.md).

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

*názevŠablona*<br/>
Vzor názvu souboru.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí ukazatel na upravený názevTemplate. Funkce vrátí **hodnotu NULL,** pokud je *názevTemplate* špatně vytvořen nebo z daného názvuTemplate nelze vytvořit žádné další jedinečné názvy.

## <a name="remarks"></a>Poznámky

Funkce **_mktemp** vytvoří jedinečný název souboru změnou argumentu *nameTemplate.* **_mktemp** podle potřeby automaticky zpracovává argumenty vícebajtových řetězců a rozpozná se sekvence vícebajtových znaků podle vícebajtové znakové stránky, která je aktuálně používána systémem run-time. **_wmktemp** je širokoznaková verze **_mktemp**; argument a vrácená hodnota **_wmktemp** jsou řetězce širokých znaků. **_wmktemp** a **_mktemp** se chovají stejně jinak, s tím rozdílem, že **_wmktemp** nezpracovává vícebajtové řetězce znaků.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

Argument *nameTemplate* má *základní*formulář XXXXXX, kde *base* je část nového názvu souboru, kterou zadáte, a každý X je zástupný symbol pro znak poskytnutý **_mktemp**. Každý zástupný znak v *názvuŠablona* musí být velké X. **_mktemp** zachová *základnu* a nahradí první koncové X abecedním znakem. **_mktemp** nahradí následující koncové X pětimístnou hodnotou; Tato hodnota je jedinečné číslo identifikující volající proces nebo v vícevláknových programech volající vlákno.

Každé úspěšné volání **_mktemp** upravuje *nameTemplate*. Při každém následném volání ze stejného procesu nebo vlákna se stejným *názvemTemplate* **argument, _mktemp** kontroluje názvy souborů, které odpovídají názvy vrácené **_mktemp** v předchozích voláních. Pokud pro daný název neexistuje žádný soubor, **_mktemp** vrátí tento název. Pokud existují soubory pro všechny dříve vrácené názvy, **_mktemp** vytvoří nový název nahrazením abecedního znaku, který použil v dříve vráceném názvu, dalším dostupným písmenem s malou písmeno v pořadí od "a" do "z". Například pokud *je základna:*

> **Fn**

a pětimístná hodnota dodaná **_mktemp** je 12345, první vrácené jméno je:

> **fna12345**

Pokud tento název se používá k vytvoření souboru FNA12345 a tento soubor stále existuje, další název vrácený při volání ze stejného procesu nebo vlákna se stejným *základem* pro *nameTemplate* je:

> **fnb12345**

Pokud FNA12345 neexistuje, další vrácený název je znovu:

> **fna12345**

**_mktemp** můžete vytvořit maximálně 26 jedinečných názvů souborů pro libovolnou kombinaci *základních* a *nameTemplate* hodnot. FnZ12345 je tedy poslední jedinečný název **souboru, _mktemp** můžete vytvořit pro *základní* a *nameTemplate* hodnoty použité v tomto příkladu.

Při selhání je **nastaveno errno.** Pokud *názevTemplate* má neplatný formát (například méně než 6 X), **errno** je nastavena na **EINVAL**. Pokud **_mktemp** nelze vytvořit jedinečný název, protože všech 26 možných názvů souborů již existuje, **_mktemp** nastaví názevTemplate na prázdný řetězec a vrátí **hodnotu EEXIST**.

V jazyce C++ mají tyto funkce přetížení šablony, které vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<io.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
