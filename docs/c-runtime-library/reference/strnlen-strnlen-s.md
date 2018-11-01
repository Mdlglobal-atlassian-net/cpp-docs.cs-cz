---
title: strnlen –, strnlen_s –, wcsnlen –, wcsnlen_s –, _mbsnlen –, _mbsnlen_l –, _mbstrnlen –, _mbstrnlen_l –
ms.date: 11/04/2016
apiname:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: f7f5050a0ab4ff0f35a28faf039688eedc2f3a8a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602563"
---
# <a name="strnlen-strnlens-wcsnlen-wcsnlens-mbsnlen-mbsnlenl-mbstrnlen-mbstrnlenl"></a>strnlen –, strnlen_s –, wcsnlen –, wcsnlen_s –, _mbsnlen –, _mbsnlen_l –, _mbstrnlen –, _mbstrnlen_l –

Získá délku řetězce pomocí aktuálního národního prostředí nebo disk, který byl předán v. Toto jsou bezpečnější verze [strlen wcslen –, _mbslen –, _mbslen_l –, _mbstrlen –, _mbstrlen_l –](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md).

> [!IMPORTANT]
> **_mbsnlen –**, **_mbsnlen_l –**, **_mbstrnlen –**, a **_mbstrnlen_l –** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*str*<br/>
Řetězec zakončený hodnotou Null.

*numberOfElements*<br/>
Velikost vyrovnávací paměti pro řetězec.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce vrátí počet znaků v řetězci, bez ukončujícího znaku null. Pokud není žádný ukončovacího znaku null v rámci první *numberOfElements* bajtů řetězce (nebo širokých znaků pro **wcsnlen –**), pak *numberOfElements* se vrátí do označuje podmínku chyby; řetězec zakončený null mají, které jsou striktně menší než *numberOfElements*.

**_mbstrnlen –** a **_mbstrnlen_l –** vrátí hodnotu -1, pokud řetězec obsahuje neplatné vícebajtového znaku.

## <a name="remarks"></a>Poznámky

> [!NOTE]
> **strnlen –** není náhradou za **strlen**; **strnlen –** je určena pro použití pouze k výpočtu velikosti příchozí nedůvěryhodná data ve vyrovnávací paměti o velikosti známé – například síťového paketu. **strnlen –** vypočítá délku, ale nebude provedou za koncem vyrovnávací paměti, pokud neukončený řetězec. U jiných situacích použijte **strlen**. (Totéž platí i pro **wcsnlen –**, **_mbsnlen –**, a **_mbstrnlen –**.)

Každá z těchto funkcí vrátí počet znaků v *str*, bez ukončujícího znaku null. Ale **strnlen –** a **strnlen_s –** interpretace řetězce jako řetězec jednobajtového znaku a proto se vrácená hodnota je vždy rovna počtu bajtů, i v případě, že řetězec obsahuje vícebajtový znaky. **wcsnlen –** a **wcsnlen_s –** jsou širokoznaké verze **strnlen –** a **strnlen_s –** ; argumenty **wcsnlen –**  a **wcsnlen_s –** jsou řetězce širokého znaku a počet znaků v jednotkách širokého znaku. V opačném případě **wcsnlen –** a **strnlen –** chovají stejně, jako tomu **strnlen_s –** a **wcsnlen_s –**.

**strnlen –**, **wcsnlen –**, a **_mbsnlen –** neověří jejich parametry. Pokud *str* je **NULL**, dojde k narušení přístupu.

**strnlen_s –** a **wcsnlen_s –** ověřují své parametry. Pokud *str* je **NULL**, funkce vrátí 0.

**_mbstrnlen –** také ověří jeho parametry. Pokud *str* je **NULL**, nebo pokud *numberOfElements* je větší než **INT_MAX**, **_mbstrnlen –** generuje výjimku neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **_mbstrnlen –** nastaví **errno** k **EINVAL** a vrátí hodnotu -1.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen –**|**strnlen –**|**strnlen –**|**wcsnlen –**|
|**_tcscnlen –**|**strnlen –**|**_mbsnlen –**|**wcsnlen –**|
|**_tcscnlen_l –**|**strnlen –**|**_mbsnlen_l**|**wcsnlen –**|

**_mbsnlen –** a **_mbstrnlen –** vrátí počet vícebajtových znaků v řetězci vícebajtového znaku. **_mbsnlen –** rozpozná vícebajtové znakové sekvence podle vícebajtovou znakovou stránku, která je aktuálně používán nebo podle národního prostředí, které je předáno; netestuje platnost vícebajtového znaku. **_mbstrnlen –** ověřuje platnost vícebajtového znaku zakončeného a rozpozná vícebajtové znakové sekvence. Pokud řetězec, který je předán **_mbstrnlen –** obsahuje platný vícebajtový znak, **errno** je nastavena na **EILSEQ**.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale _wsetlocale](setlocale-wsetlocale.md) Další informace. Verze těchto funkcí jsou identické, s tím rozdílem, ty, které nemají mít **_l** přípona používají aktuální národní prostředí pro toto chování závislé na národním prostředí a verze, které mají **_l** příponu Místo toho používá parametr národního prostředí, které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strnlen –**, **strnlen_s –**|\<String.h >|
|**wcsnlen –**, **wcsnlen_s –**|\<String.h > nebo \<wchar.h >|
|**_mbsnlen –**, **_mbsnlen_l –**|\<Mbstring.h >|
|**_mbstrnlen –**, **_mbstrnlen_l –**|\<stdlib.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

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
