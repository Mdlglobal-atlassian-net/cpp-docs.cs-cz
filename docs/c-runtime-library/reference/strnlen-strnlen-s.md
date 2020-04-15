---
title: strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l
ms.date: 4/2/2020
api_name:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
- _o__mbsnlen
- _o__mbsnlen_l
- _o__mbstrnlen
- _o__mbstrnlen_l
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
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
ms.openlocfilehash: db4fa65fa47dfe11d7ab56ffc5feee06f2634e2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364460"
---
# <a name="strnlen-strnlen_s-wcsnlen-wcsnlen_s-_mbsnlen-_mbsnlen_l-_mbstrnlen-_mbstrnlen_l"></a>strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l

Získá délku řetězce pomocí aktuální národní prostředí nebo ten, který byl předán. Jedná se o bezpečnější verze [strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md).

> [!IMPORTANT]
> **_mbsnlen**, **_mbsnlen_l**, **_mbstrnlen**a **_mbstrnlen_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
size_t strnlen(
   const char *str,
   size_t numberOfElements
);
size_t strnlen_s(
   const char *str,
   size_t numberOfElements
);
size_t wcsnlen(
   const wchar_t *str,
   size_t numberOfElements
);
size_t wcsnlen_s(
   const wchar_t *str,
   size_t numberOfElements
);
size_t _mbsnlen(
   const unsigned char *str,
   size_t numberOfElements
);
size_t _mbsnlen_l(
   const unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
size_t _mbstrnlen(
   const char *str,
   size_t numberOfElements
);
size_t _mbstrnlen_l(
   const char *str,
   size_t numberOfElements,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Řetězec ukončený hodnotou Null.

*numberOfElements*<br/>
Velikost vyrovnávací paměti řetězce.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce vrátí počet znaků v řetězci, bez ukončení znaku null. Pokud neexistuje žádný null zakončení v rámci první *numberOfElements* bajtů řetězce (nebo široké znaky pro **wcsnlen**), pak *numberOfElements* je vrácena k označení chybové podmínky; řetězce s ukončeným hodnotou null mají délky, které jsou přísně menší než *numberOfElements*.

**_mbstrnlen** a **_mbstrnlen_l** vrátí -1, pokud řetězec obsahuje neplatný vícebajtový znak.

## <a name="remarks"></a>Poznámky

> [!NOTE]
> **strnlen** není náhradou za **strlen**; **Strnlen** je určen pouze k výpočtu velikosti příchozích nedůvěryhodných dat ve vyrovnávací paměti známé velikosti – například síťového paketu. **strnlen** vypočítá délku, ale neprochází kolem konce vyrovnávací paměti, pokud je řetězec neukončený. V jiných situacích použijte **strlen**. (Totéž platí pro **wcsnlen**, **_mbsnlen**a **_mbstrnlen**.)

Každá z těchto funkcí vrátí počet znaků v *str*, bez ukončení znaku null. **Strnlen** a **strnlen_s** však interpretovat řetězec jako jednobajtový znakový řetězec a proto je vrácená hodnota vždy rovna počtu bajtů, i když řetězec obsahuje vícebajtové znaky. **wcsnlen** a **wcsnlen_s** jsou širokoznakové verze **strnlen** a **strnlen_s;** argumenty pro **wcsnlen** a **wcsnlen_s** jsou řetězce s širokými znaky a počet znaků je v jednotkách s širokými znaky. V opačném případě se **wcsnlen** a **strnlen** chovají stejně, stejně jako **strnlen_s** a **wcsnlen_s**.

**strnlen**, **wcsnlen**a **_mbsnlen** neověřují své parametry. Pokud *str* je **NULL**, dojde k narušení přístupu.

**strnlen_s** a **wcsnlen_s** ověřit jejich parametry. Pokud *str* je **NULL**, funkce vrátí 0.

**_mbstrnlen** také ověřuje jeho parametry. Pokud *str* je **NULL**, nebo *pokud numberOfElements* je větší než **INT_MAX**, **_mbstrnlen** generuje neplatný parametr výjimku, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, **_mbstrnlen** nastaví **errno** na **EINVAL** a vrátí -1.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen** a **_mbstrnlen** vrátí počet vícebajtových znaků v řetězci vícebajtových znaků. **_mbsnlen** rozpozná vícebajtové sekvence znaků podle vícebajtové znakové stránky, která je aktuálně používána, nebo podle předávaného národního prostředí; netestuje platnost vícebajtového znaku. **_mbstrnlen** testy pro platnost vícebajtových znaků a rozpozná vícebajtové sekvence znaků. Pokud řetězec, který je předán **_mbstrnlen** obsahuje neplatný vícebajtový znak, **je errno** nastaveno na **EILSEQ**.

Výstupní hodnota je ovlivněna nastavením nastavení **LC_CTYPE** kategorie národního prostředí; další informace naleznete [v _wsetlocale setlocale.](setlocale-wsetlocale.md) Verze těchto funkcí jsou identické, s tím rozdílem, že ty, které nemají **_l** příponu použít aktuální národní prostředí pro toto chování závislé na národním prostředí a verze, které mají **příponu _l** místo toho použít parametr národního prostředí, který je předán. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strnlen**, **strnlen_s**|\<string.h>|
|**wcsnlen**, **wcsnlen_s**|\<string.h> \<nebo wchar.h>|
|**_mbsnlen** **_mbsnlen_l**|\<mbstring.h>|
|**_mbstrnlen**, **_mbstrnlen_l**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strnlen.c

#include <string.h>

int main()
{
   // str1 is 82 characters long. str2 is 159 characters long

   char* str1 = "The length of a string is the number of characters\n"
               "excluding the terminating null.";
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"
                "than the maximum size specified, the maximum size is\n"
                "returned rather than the actual size of the string.";
   size_t len;
   size_t maxsize = 100;

   len = strnlen(str1, maxsize);
   printf("%s\n Length: %d \n\n", str1, len);

   len = strnlen(str2, maxsize);
   printf("%s\n Length: %d \n", str2, len);
}
```

```Output
The length of a string is the number of characters
excluding the terminating null.
Length: 82

strnlen takes a maximum size. If the string is longer
than the maximum size specified, the maximum size is
returned rather than the actual size of the string.
Length: 100
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
