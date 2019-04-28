---
title: _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l
ms.date: 11/04/2016
apiname:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: d27b2128d79d7ff3ab0150e182d494fed52d46ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353832"
---
# <a name="stricmp-wcsicmp-mbsicmp-stricmpl-wcsicmpl-mbsicmpl"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l

Provádí porovnávání řetězců.

> [!IMPORTANT]
> **_mbsicmp –** a **_mbsicmp_l –** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*string1*, *string2*<br/>
Řetězec zakončený hodnotou Null pro srovnání.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota označuje vztah *řetězec1* k *řetězec2* následujícím způsobem.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|*řetězec1* menší než *řetězec2*|
|0|*řetězec1* shodné s *řetězec2*|
|> 0|*řetězec1* větší než *řetězec2*|

V případě chyby **_mbsicmp –** vrátí **_NLSCMPERROR**, který je definován v \<string.h > a \<mbstring.h >.

## <a name="remarks"></a>Poznámky

**_Stricmp –** funkce ordinally porovná *řetězec1* a *řetězec2* po převedení jednotlivé znaky na malá písmena a vrátí hodnotu, která jejich vztahu. **_stricmp –** se liší od **_stricoll –** v tom, že **_stricmp –** porovnání pouze ovlivněny **LC_CTYPE**, který určuje, jaké znaky jsou nahoře a malá písmena. **_Stricoll –** funkce porovná řetězce podle i **LC_CTYPE** a **LC_COLLATE** kategorie národního prostředí, včetně případu a řazení pořadí. Další informace o **LC_COLLATE** kategorie, naleznete v tématu [setlocale](setlocale-wsetlocale.md) a [kategorie národního prostředí](../../c-runtime-library/locale-categories.md). Verze těchto funkcí bez **_l** přípona používají aktuální národní prostředí pro chování závislé na národním prostředí. Verze s příponou jsou identické, s tím rozdílem, že používají předané národní prostředí. Pokud není nastavený národní prostředí, používá se národní prostředí jazyka C. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

> [!NOTE]
> **_stricmp –** je ekvivalentní **_strcmpi –**. Můžete třeba používat Zaměnitelně, ale **_stricmp –** je preferovaný standard.

**_Strcmpi –** funkce je ekvivalentní volání **_stricmp –** a je k dispozici pouze z důvodů zpětné kompatibility.

Protože **_stricmp –** malá porovnání, může způsobit neočekávané chování.

Pro ilustraci při převodu podle malá a velká **_stricmp –** ovlivní výsledek porovnání, se předpokládá, že máte dva řetězce JOHNSTON a JOHN_HENRY. JOHNSTON řetězec JOHN_HENRY se budou považovat za méně než protože "_" má hodnotu ASCII nižší než malá S. Ve skutečnosti libovolný znak, který má hodnotu ASCII 91 až 96 se budou považovat za méně než nabízí jakýkoli písmeno.

Pokud [strcmp –](strcmp-wcscmp-mbscmp.md) funkce se použije namísto **_stricmp –**, bude větší než JOHNSTONOVY JOHN_HENRY.

**_wcsicmp –** a **_mbsicmp –** jsou širokoznaké a vícebajtové verze **_stricmp –**. Argumenty a vrácené hodnoty **_wcsicmp –** jsou širokoznaké řetězce **_mbsicmp –** jsou vícebajtové znakové řetězce. **_mbsicmp –** rozpozná vícebajtové znakové sekvence podle aktuální vícebajtové znakové stránce a vrátí **_NLSCMPERROR** v případě chyby. Další informace najdete v tématu [znakové stránky](../../c-runtime-library/code-pages.md). Tyto tři funkce chovají identicky jinak.

**_wcsicmp –** a **wcscmp –** chovají stejně, s výjimkou, že **wcscmp –** nepřevádí argumenty na malá písmena před jejich porovnání. **_mbsicmp –** a **_mbscmp –** chovají stejně, s výjimkou, že **_mbscmp –** nepřevádí argumenty na malá písmena před jejich porovnání.

Je potřeba volat [setlocale](setlocale-wsetlocale.md) pro **_wcsicmp –** pro práci s Latin 1 znaků. Národní prostředí jazyka C je výsledkem bude ve výchozím nastavení, tedy například ä nesmí rovnat Ä. Volání **setlocale** s všechna národní prostředí kromě národní prostředí jazyka C před voláním **_wcsicmp –**. Následující příklad ukazuje, jak **_wcsicmp –** je citlivé na národní prostředí:

```C
// crt_stricmp_locale.c
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

Alternativou je volání [_create_locale _wcreate_locale](create-locale-wcreate-locale.md) a předejte objekt vrácený národního prostředí jako parametr **_wcsicmp_l –**.

Všechny tyto funkce ověřují své parametry. Pokud *řetězec1* nebo *řetězec2* jsou ukazatelé s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, vrátí tyto funkce **_NLSCMPERROR** a nastavte **errno** k **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_stricmp**, **_stricmp_l**|\<string.h>|
|**_wcsicmp**, **_wcsicmp_l**|\<String.h > nebo \<wchar.h >|
|**_mbsicmp**, **_mbsicmp_l**|\<Mbstring.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

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
