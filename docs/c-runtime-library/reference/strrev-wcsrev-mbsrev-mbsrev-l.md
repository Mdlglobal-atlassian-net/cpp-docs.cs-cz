---
title: _strrev, _wcsrev, _mbsrev, _mbsrev_l
ms.date: 4/2/2020
api_name:
- _wcsrev
- _mbsrev
- _strrev
- _mbsrev_l
- _o__mbsrev
- _o__mbsrev_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _strrev
- _ftcsrev
- _tcsrev
- mbsrev
- mbsrev_l
- _wcsrev_fstrrev
- _mbsrev
helpviewer_keywords:
- _mbsrev_l function
- characters [C++], switching
- _mbsrev function
- strrev function
- _ftcsrev function
- strings [C++], reversing
- wcsrev function
- _strrev function
- mbsrev_l function
- reversing characters in strings
- ftcsrev function
- characters [C++], reversing order
- _wcsrev function
- mbsrev function
- tcsrev function
- _tcsrev function
ms.assetid: 87863e89-4fa0-421c-af48-25d8516fe72f
ms.openlocfilehash: 585cdae15572eca565d2779225737a014d5f7837
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365032"
---
# <a name="_strrev-_wcsrev-_mbsrev-_mbsrev_l"></a>_strrev, _wcsrev, _mbsrev, _mbsrev_l

Obrátí znaky řetězce.

> [!IMPORTANT]
> **_mbsrev** a **_mbsrev_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strrev(
   char *str
);
wchar_t *_wcsrev(
   wchar_t *str
);
unsigned char *_mbsrev(
   unsigned char *str
);
unsigned char *_mbsrev_l(
   unsigned char *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Řetězec ukončený hodnotou null, který má být stornován.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na změněný řetězec. Žádná vrácená hodnota je vyhrazena k označení chyby.

## <a name="remarks"></a>Poznámky

Funkce **_strrev** obrátí pořadí znaků v *str*. Ukončující znak null zůstane na místě. **_wcsrev** a **_mbsrev** jsou verze **_strrev**s širokými znaky a vícebajtovými znaky . Argumenty a vrácená hodnota **_wcsrev** jsou řetězce širokých znaků; _mbsrev **jsou** řetězce vícebajtových znaků. U **_mbsrev**se pořadí bajtů v každém vícebajtovém znaku v *str* nezmění. Tyto tři funkce se chovají stejně jinak.

**_mbsrev** ověří jeho parametry. Pokud je *buď string1* nebo *string2* ukazatel null, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **vrátí _mbsrev** **hodnotu NULL** a nastaví **errno** na **EINVAL**. **_strrev** a **_wcsrev** neověřují jejich parametry.

Výstupní hodnota je ovlivněna nastavením nastavení **LC_CTYPE** kategorie národního prostředí; další informace naleznete [v _wsetlocale setlocale.](setlocale-wsetlocale.md) Verze těchto funkcí jsou identické, s tím rozdílem, že ty, které nemají **_l** příponu použít aktuální národní prostředí a ty, které mají **příponu _l** místo toho použít parametr národního prostředí, který je předán. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

> [!IMPORTANT]
> Tyto funkce mohou být náchylné k hrozbám přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti lze použít pro systémové útoky, protože mohou způsobit neoprávněné zvýšení oprávnění. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsrev**|**_strrev**|**_mbsrev**|**_wcsrev**|
|**N/a**|**N/a**|**_mbsrev_l**|**N/a**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strrev**|\<string.h>|
|**_wcsrev**|\<string.h> \<nebo wchar.h>|
|**_mbsrev** **_mbsrev_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strrev.c
// This program checks a string to see
// whether it is a palindrome: that is, whether
// it reads the same forward and backward.
//

#include <string.h>
#include <stdio.h>

int main( void )
{
   char* string = "Able was I ere I saw Elba";
   int result;

   // Reverse string and compare (ignore case):
   result = _stricmp( string, _strrev( _strdup( string ) ) );
   if( result == 0 )
      printf( "The string \"%s\" is a palindrome\n", string );
   else
      printf( "The string \"%s\" is not a palindrome\n", string );
}
```

```Output
The string "Able was I ere I saw Elba" is a palindrome
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
