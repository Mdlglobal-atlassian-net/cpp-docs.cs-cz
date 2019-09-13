---
title: _mktemp, _wmktemp
ms.date: 11/04/2016
api_name:
- _wmktemp
- _mktemp
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
ms.openlocfilehash: 7cfca04d4f0df2673a2221f00a1263f73e8516ec
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951581"
---
# <a name="_mktemp-_wmktemp"></a>_mktemp, _wmktemp

Vytvoří jedinečný název souboru. K dispozici jsou bezpečnější verze těchto funkcí; viz [_mktemp_s, _wmktemp_s](mktemp-s-wmktemp-s.md).

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
Vzor názvu souboru.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na upravený nameTemplate. Funkce vrátí **hodnotu null** , pokud je *nameTemplate* špatně vytvořená nebo nelze vytvořit více jedinečných názvů z daného nameTemplate.

## <a name="remarks"></a>Poznámky

Funkce **_mktemp** vytvoří jedinečný název souboru úpravou argumentu *nameTemplate* . **_mktemp** automaticky zpracovává argumenty vícebajtového řetězce znaků podle potřeby a rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která je aktuálně používána systémem za běhu. **_wmktemp** je **_mktemp**verze s velkým znakem; argument a návratová hodnota **_wmktemp** jsou řetězce s velkým počtem znaků. **_wmktemp** a **_mktemp** se chovají identicky jinak, s tím rozdílem, že **_wmktemp** zpracovává řetězce vícebajtových znaků.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

Argument *nameTemplate* má notaci *Base*XXXXXX, kde *Base* je část nového názvu souboru, kterou zadáte, a každá X je zástupný symbol pro znak dodaný **_mktemp**. Každý zástupný znak v *nameTemplate* musí být velkými písmeny x. **_mktemp** , který zachovává *základ* , a nahradí první koncový znak x znakem abecedy. **_mktemp** nahrazuje následující koncový znak X s hodnotou s pěti číslicemi; Tato hodnota je jedinečné číslo identifikující volající proces nebo ve vícevláknových programech, volajícím vlákně.

Každé úspěšné volání **_mktemp** mění *nameTemplate*. V každém následném volání ze stejného procesu nebo vlákna se stejným argumentem *nameTemplate* **_mktemp** kontroluje názvy souborů, které odpovídají názvům vráceným funkcí **_mktemp** v předchozích voláních. Pokud pro daný název neexistují žádné soubory, **_mktemp** tento název vrátí. Pokud soubory existují u všech dříve vrácených názvů, **_mktemp** vytvoří nový název nahrazením abecedního znaku, který se použil v dříve vráceném názvu, s následujícím dostupným malým malým písmenem, v pořadí od a do z. Například pokud je *základní* :

> **VistaScan**

a hodnota s pěti číslicemi, kterou poskytuje **_mktemp** , je 12345, jméno, které se vrátí, je:

> **fna12345**

Pokud se tento název používá k vytvoření souboru FNA12345 a tento soubor stále existuje, další název vrácený při volání ze stejného procesu nebo vlákna se stejným *základem* pro *nameTemplate* je:

> **fnb12345**

Pokud FNA12345 neexistuje, vrátí se další název znovu:

> **fna12345**

**_mktemp** může vytvořit maximálně 26 jedinečných názvů souborů pro všechny dané kombinace *základních* a *nameTemplate* hodnot. Proto je FNZ12345 poslední jedinečný název souboru **_mktemp** může vytvořit pro *základní* a *nameTemplate* hodnoty použité v tomto příkladu.

Při selhání se nastaví **errno** . Pokud má *nameTemplate* neplatný formát (například méně než 6 X), **errno** je nastaven na **EINVAL**. Pokud **_mktemp** nemůže vytvořit jedinečný název, protože již existují všechny 26 možné názvy souborů, **_mktemp** nastaví nameTemplate na prázdný řetězec a vrátí **EEXIST**.

V C++nástroji mají tyto funkce přetížení šablony, které vyvolávají novější a zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<IO. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
