---
title: _mktemp_s, _wmktemp_s
ms.date: 11/04/2016
api_name:
- _mktemp_s
- _wmktemp_s
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
ms.openlocfilehash: 464f0dfbdb0b84e1fd29ec650e53f5c2543c4403
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624213"
---
# <a name="_mktemp_s-_wmktemp_s"></a>_mktemp_s, _wmktemp_s

Vytvoří jedinečný název souboru. Jedná se o verze [_mktemp, _wmktemp](mktemp-wmktemp.md) s vylepšeními zabezpečení, jak [je popsáno v části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Vzor názvu souboru.

*sizeInChars*<br/>
Velikost vyrovnávací paměti v jednobajtových znacích v **_mktemp_s**; velké znaky v **_wmktemp_s**, včetně ukončovacího znaku null.

## <a name="return-value"></a>Návratová hodnota

Obě tyto funkce vrátí nulu při úspěchu; chybový kód při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*nameTemplate*|*sizeInChars*|Návratová hodnota|Nová hodnota v *nameTemplate*|
|----------------|-------------------|----------------------|-------------------------------|
|**PLATNOST**|Jakýmikoli|**EINVAL**|**PLATNOST**|
|Nesprávný formát (pro správný formát viz oddíl poznámky)|Jakýmikoli|**EINVAL**|Prázdný řetězec|
|Jakýmikoli|< = počet X|**EINVAL**|Prázdný řetězec|

Pokud dojde k některé z výše uvedených chybových podmínek, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_mktemp_s** vytvoří jedinečný název souboru úpravou argumentu *nameTemplate* , aby po volání odkazoval ukazatel *nameTemplate* na řetězec obsahující nový název souboru. **_mktemp_s** automaticky zpracovává argumenty vícebajtového řetězce znaků podle potřeby a rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která je aktuálně používána systémem za běhu. **_wmktemp_s** je **_mktemp_s**verze s velkým znakem; argumentem **_wmktemp_s** je řetězec s velkým počtem znaků. **_wmktemp_s** a **_mktemp_s** se chovají identicky jinak, s tím rozdílem, že **_wmktemp_s** zpracovává řetězce vícebajtových znaků.

Verze knihovny ladění těchto funkcí nejprve naplní vyrovnávací paměť pomocí 0xFE. Pokud chcete toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

Argument *nameTemplate* má formu **baseXXXXXX**, kde *Base* je součást nového názvu souboru, kterou zadáte, a každá X je zástupný symbol pro znak dodaný **_mktemp_s**. Každý zástupný znak v *nameTemplate* musí být velkými písmeny x. **_mktemp_s** , který zachovává *základ* , a nahradí první koncový znak x znakem abecedy. **_mktemp_s** nahrazuje následující koncový znak X s hodnotou s pěti číslicemi; Tato hodnota je jedinečné číslo identifikující volající proces nebo ve vícevláknových programech, volajícím vlákně.

Každé úspěšné volání **_mktemp_s** mění *nameTemplate*. V každém následném volání ze stejného procesu nebo vlákna se stejným argumentem *nameTemplate* **_mktemp_s** kontroluje názvy souborů, které odpovídají názvům vráceným funkcí **_mktemp_s** v předchozích voláních. Pokud pro daný název neexistují žádné soubory, **_mktemp_s** tento název vrátí. Pokud soubory existují u všech dříve vrácených názvů, **_mktemp_s** vytvoří nový název nahrazením abecedního znaku, který se použil v dříve vráceném názvu, s následujícím dostupným malým malým písmenem, v pořadí od a do z. Například pokud je *základní* :

> **VistaScan**

a hodnota s pěti číslicemi, kterou poskytuje **_mktemp_s** , je 12345, jméno, které se vrátí, je:

> **fna12345**

Pokud se tento název používá k vytvoření souboru FNA12345 a tento soubor stále existuje, další název vrácený při volání ze stejného procesu nebo vlákna se stejným *základem* pro *nameTemplate* je:

> **fnb12345**

Pokud FNA12345 neexistuje, vrátí se další název znovu:

> **fna12345**

**_mktemp_s** může vytvořit maximálně 26 jedinečných názvů souborů pro všechny dané kombinace *základních* a *nameTemplate* hodnot. Proto je FNZ12345 poslední jedinečný název souboru **_mktemp_s** může vytvořit pro *základní* a *nameTemplate* hodnoty použité v tomto příkladu.

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mktemp_s**|\<IO. h >|
|**_wmktemp_s**|\<IO. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
