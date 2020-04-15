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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 315a86c5cf7e58219bad25f2b6633dd91275c09f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320461"
---
# <a name="_stricmp-_wcsicmp-_mbsicmp-_stricmp_l-_wcsicmp_l-_mbsicmp_l"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l

Provede porovnání řetězců bez rozlišování velkých a malých písmen.

> [!IMPORTANT]
> **_mbsicmp** a **_mbsicmp_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Řetězce ukončené hodnotou null k porovnání.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota označuje vztah *string1* k *string2* následujícím způsobem.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|*string1* menší než *string2*|
|0|*string1* identické s *string2*|
|> 0|*string1* větší než *string2*|

Při chybě **vrátí _mbsicmp** **_NLSCMPERROR**, \<který je definován \<v> string.h> a mbstring.h.

## <a name="remarks"></a>Poznámky

Funkce **_stricmp** řadově porovná *string1* a *string2* po převodu každého znaku na malá písmena a vrátí hodnotu označující jejich vztah. **_stricmp** se liší od **_stricoll** v tom, že **porovnání _stricmp** je ovlivněno pouze **LC_CTYPE**, která určuje, které znaky jsou velká a malá písmena. Funkce **_stricoll** porovnává řetězce podle **LC_CTYPE** a **LC_COLLATE** kategorie národního prostředí, která zahrnuje případ i pořadí řazení. Další informace o **kategorii LC_COLLATE** naleznete v tématu [setlocale](setlocale-wsetlocale.md) a [Locale Categories](../../c-runtime-library/locale-categories.md). Verze těchto funkcí bez **přípony _l** používají aktuální národní prostředí pro chování závislé na národním prostředí. Verze s příponou jsou identické s tím rozdílem, že místo toho používají národní prostředí předané. Pokud národní prostředí nebylo nastaveno, národní prostředí C se používá. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

> [!NOTE]
> **_stricmp** odpovídá **_strcmpi**. Mohou být použity zaměnitelně, ale **_stricmp** je preferovaným standardem.

Funkce **_strcmpi** je ekvivalentní **_stricmp** a je k dispozici pouze pro zpětnou kompatibilitu.

Vzhledem k tomu, **že _stricmp** porovnání malá písmena, může mít za následek neočekávané chování.

Pro ilustraci při převodu případu **_stricmp** ovlivňuje výsledek porovnání, předpokládejme, že máte dva řetězce JOHNSTON a JOHN_HENRY. Řetězec JOHN_HENRY bude považován za menší než JOHNSTON, protože "_" má nižší hodnotu ASCII než malé Písmeno S. Ve skutečnosti každý znak, který má hodnotu ASCII mezi 91 a 96 budou považovány za menší než jakékoli písmeno.

Pokud je místo **_stricmp**použita funkce [strcmp](strcmp-wcscmp-mbscmp.md) , bude JOHN_HENRY větší než JOHNSTON.

**_wcsicmp** a **_mbsicmp** jsou verze **_stricmp**s širokými znaky a vícebajtovými znaky . Argumenty a vrácená hodnota **_wcsicmp** jsou řetězce širokých znaků; **_mbsicmp** jsou vícebajtové řetězce znaků. **_mbsicmp** rozpoznává vícebajtové sekvence znaků podle aktuální znakové stránky vícebajtů a vrací **_NLSCMPERROR** na chybu. Další informace naleznete v [tématu Code Pages](../../c-runtime-library/code-pages.md). Tyto tři funkce se chovají stejně jinak.

**_wcsicmp** a **wcscmp** se chovají stejně s tím rozdílem, že **wcscmp** nepřevede své argumenty na malá písmena před jejich porovnáním. **_mbsicmp** a **_mbscmp** se chovají stejně s tím rozdílem, že **_mbscmp** nepřevede své argumenty na malá písmena před jejich porovnáním.

Budete muset volat [setlocale](setlocale-wsetlocale.md) pro **_wcsicmp** pro práci s latinkou 1 znaků. Národní prostředí C je ve výchozím nastavení platné, takže například ä nebude porovnávat rovno Ä. Volání **setlocale** s libovolným národním prostředím než národní prostředí C před voláním **_wcsicmp**. Následující ukázka **ukazuje,** jak je _wcsicmp citlivé na národní prostředí:

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

Alternativou je volání [_create_locale, _wcreate_locale](create-locale-wcreate-locale.md) a předat vrácený objekt národního prostředí jako parametr **_wcsicmp_l**.

Všechny tyto funkce ověřují jejich parametry. Pokud *jsou buď string1* nebo *string2* ukazatele null, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je spuštění povoleno pokračovat, tyto funkce vrátí **_NLSCMPERROR** a nastaví **errno** na **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_stricmp**, **_stricmp_l**|\<string.h>|
|**_wcsicmp**, **_wcsicmp_l**|\<string.h> \<nebo wchar.h>|
|**_mbsicmp**, **_mbsicmp_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
