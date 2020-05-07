---
title: _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l
ms.date: 4/2/2020
api_name:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
- _o__mbsicmp
- _o__mbsicmp_l
- _o__stricmp
- _o__stricmp_l
- _o__wcsicmp
- _o__wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftcsicmp
- _stricmp
- wcsicmp_l
- _wcsicmp
- _tcsicmp
- _strcmpi
- stricmp_l
- _mbsicmp
- _fstricmp
- mbsicmp_l
- mbsicmp
helpviewer_keywords:
- _wcsicmp function
- _stricmp_l function
- fstricmp function
- _tcsicmp function
- ftcsicmp function
- string comparison [C++], lowercase
- _wcsicmp_l function
- _fstricmp function
- strings [C++], comparing
- mbsicmp function
- _ftcsicmp function
- _mbsicmp_l function
- wcsicmp_l function
- _stricmp function
- _mbsicmp function
- tcsicmp function
- stricmp_l function
- mbsicmp_l function
- _strcmpi function
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
ms.openlocfilehash: 786c2bd2738bb82b3edac5c811ccfd3f9f8bc854
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920013"
---
# <a name="_stricmp-_wcsicmp-_mbsicmp-_stricmp_l-_wcsicmp_l-_mbsicmp_l"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l

Provede porovnání řetězců bez rozlišování velkých a malých písmen.

> [!IMPORTANT]
> **_mbsicmp** a **_mbsicmp_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _stricmp(
   const char *string1,
   const char *string2
);
int _wcsicmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricmp_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*řetězec1*, *řetězec2*<br/>
Řetězec zakončený hodnotou null k porovnání

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota označuje vztah *řetězec1* na *řetězec2* následujícím způsobem.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|*řetězec1* menší než *řetězec2*|
|0|*řetězec1* totožný s *řetězec2*|
|> 0|*řetězec1* větší než *řetězec2*|

Při chybě **_mbsicmp** vrátí **_NLSCMPERROR**, která je definována v \<řetězci. h> a \<Mbstring. h>.

## <a name="remarks"></a>Poznámky

Funkce **_stricmp** pořadová čísla *řetězec1* a *řetězec2* porovnává po převodu jednotlivých znaků na malá písmena a vrátí hodnotu, která označuje jejich relaci. **_stricmp** se liší od **_stricoll** v tom, že porovnání **_stricmp** je ovlivněno pouze **LC_CTYPE**, které určuje, které znaky jsou velká a malá písmena. Funkce **_stricoll** porovnává řetězce v závislosti na kategoriích **LC_CTYPE** a **LC_COLLATE** národního prostředí, které zahrnuje i pořadí řazení v obou případech. Další informace o kategorii **LC_COLLATE** naleznete v tématu [setlocale](setlocale-wsetlocale.md) and [locale Categories](../../c-runtime-library/locale-categories.md). Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro chování závislé na národním prostředí. Verze s příponou jsou stejné s tím rozdílem, že místo toho používají předané národní prostředí. Pokud národní prostředí nebylo nastaveno, použije se národní prostředí jazyka C. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

> [!NOTE]
> **_stricmp** je ekvivalentem **_strcmpi**. Je možné je použít zaměnitelné, ale **_stricmp** je upřednostňovaným standardem.

Funkce **_strcmpi** je ekvivalentní **_stricmp** a je k dispozici pouze pro zpětnou kompatibilitu.

Protože **_stricmp** provádí porovnávání malých a velkých písmen, může to vést k neočekávanému chování.

K ilustraci, když převod velkých a malých písmen pomocí **_stricmp** ovlivňuje výsledek porovnání, Předpokládejme, že máte dva řetězce JOHNSTON a JOHN_HENRY. Řetězec JOHN_HENRY bude považován za menší než JOHNSTON, protože "_" má nižší hodnotu ASCII než malé písmeno S. Každý znak, který má hodnotu ASCII mezi 91 a 96, bude považován za méně než jakékoli písmeno.

Pokud se místo **_stricmp**použije funkce [strcmp](strcmp-wcscmp-mbscmp.md) , JOHN_HENRY bude větší než Johnston.

**_wcsicmp** a **_mbsicmp** jsou verze **_stricmp**a vícebajtových znaků. Argumenty a návratová hodnota **_wcsicmp** jsou řetězce s velkým počtem znaků; **_mbsicmp** jsou vícebajtové znakové řetězce. **_mbsicmp** rozpozná vícebajtové znakové sekvence podle aktuální vícebajtové znakové stránky a vrátí **_NLSCMPERROR** při chybě. Další informace najdete v tématu [znakové stránky](../../c-runtime-library/code-pages.md). Tyto tři funkce se chovají identicky jinak.

**_wcsicmp** a **wcscmp** se chovají stejně, s výjimkou, že **wcscmp** nepřevede své argumenty na malá písmena, než je porovnáte. **_mbsicmp** a **_mbscmp** se chovají stejně, s výjimkou toho, že **_mbscmp** nepřevádějí své argumenty na malá písmena před jejich porovnáním.

Pokud chcete pracovat s latinkou 1 znaky, budete muset zavolat [setlocali](setlocale-wsetlocale.md) pro **_wcsicmp** . Národní prostředí jazyka C je ve výchozím nastavení platné, takže například ä se nerovná se Ä. Před voláním **_wcsicmp**volejte **setlocale** s jakýmkoli národním prostředím jiným než národním prostředím C. Následující příklad ukazuje, jak je **_wcsicmp** citlivá na národní prostředí:

```C
// crt_stricmp_locale.c
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <string.h>
#include <stdio.h>
#include <locale.h>

int main() {
   setlocale(LC_ALL,"C");   // in effect by default
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails
   setlocale(LC_ALL,"");
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds
}
```

Alternativou je volání [_create_locale, _wcreate_locale](create-locale-wcreate-locale.md) a předání vráceného objektu národního prostředí jako parametru do **_wcsicmp_l**.

Všechny tyto funkce ověřují své parametry. Pokud je parametr *řetězec1* nebo *řetězec2* ukazateli s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, vrátí tyto funkce **_NLSCMPERROR** a nastaví **errno** na **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_stricmp** **_stricmp_l**|\<String. h>|
|**_wcsicmp** **_wcsicmp_l**|\<String. h> nebo \<WCHAR. h>|
|**_mbsicmp** **_mbsicmp_l**|\<Mbstring. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_stricmp.c

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown dog jumps over the lazy fox";

int main( void )
{
   char tmp[20];
   int result;

   // Case sensitive
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );
   result = strcmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
   The quick brown dog jumps over the lazy fox
   The QUICK brown dog jumps over the lazy fox

   strcmp:   String 1 is greater than string 2
   _stricmp:  String 1 is equal to string 2
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
