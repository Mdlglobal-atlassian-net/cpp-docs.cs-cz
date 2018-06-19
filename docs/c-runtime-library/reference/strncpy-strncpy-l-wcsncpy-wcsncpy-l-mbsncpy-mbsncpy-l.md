---
title: strncpy –, _strncpy_l –, wcsncpy –, _wcsncpy_l –, _mbsncpy –, _mbsncpy_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strncpy
- _strncpy_l
- _mbsncpy
- wcsncpy
- _mbsncpy_l
- _wcsncpy_l
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
- _fstrncpy
- strncpy
- _ftcsncpy
- _tcsnccpy_l
- _tcsnccpy
- _mbsncpy
- wcsncpy
- _tcsncpy
- _strncpy_l
- _mbsncpy_l
- _wcsncpy_l
dev_langs:
- C++
helpviewer_keywords:
- wcsncpy_l function
- characters [C++], copying
- mbsncpy_l function
- strncpy_l function
- wcsncpy function
- tcsnccpy function
- ftcsncpy function
- copying characters of strings
- _wcsncpy_l function
- _tcsnccpy function
- _tcsnccpy_l function
- strncpy function
- _tcsncpy function
- mbsncpy function
- _fstrncpy function
- _mbsncpy_l function
- tcsncpy_l function
- tcsnccpy_l function
- fstrncpy function
- strings [C++], copying
- _ftcsncpy function
- _tcsncpy_l function
- _mbsncpy function
- tcsncpy function
- _strncpy_l function
ms.assetid: ac4345a1-a129-4f2f-bb8a-373ec58ab8b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4b4ec53451b750e92d952a57257709e9a0cde09
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418234"
---
# <a name="strncpy-strncpyl-wcsncpy-wcsncpyl-mbsncpy-mbsncpyl"></a>strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l

Kopírování znaků řetězce do jiného. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [strncpy_s –, _strncpy_s_l –, wcsncpy_s –, _wcsncpy_s_l –, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md).

> [!IMPORTANT]
> **_mbsncpy –** a **_mbsncpy_l –** nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strncpy(
   char *strDest,
   const char *strSource,
   size_t count
);
char *_strncpy_l(
   char *strDest,
   const char *strSource,
   size_t count,
   locale_t locale
);
wchar_t *wcsncpy(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
wchar_t *_wcsncpy_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   locale_t locale
);
unsigned char *_mbsncpy(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count
);
unsigned char *_mbsncpy_l(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
char *strncpy(
   char (&strDest)[size],
   const char *strSource,
   size_t count
); // C++ only
template <size_t size>
char *_strncpy_l(
   char (&strDest)[size],
   const char *strSource,
   size_t count,
   locale_t locale
); // C++ only
template <size_t size>
wchar_t *wcsncpy(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count
); // C++ only
template <size_t size>
wchar_t *_wcsncpy_l(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count,
   locale_t locale
); // C++ only
template <size_t size>
unsigned char *_mbsncpy(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsncpy_l(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*strDest*<br/>
Cílový řetězec.

*strSource*<br/>
Zdrojový řetězec.

*Počet*<br/>
Počet znaků, které se mají zkopírovat.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Vrátí *strDest*. Žádnou návratovou hodnotu je vyhrazena indikující chybu.

## <a name="remarks"></a>Poznámky

**Strncpy –** funkce zkopíruje počáteční *počet* znaků *strSource* k *strDest* a vrátí *strDest* . Pokud *počet* je menší než nebo rovna délce *strSource*, znak hodnoty null nejsou automaticky připojeny k zkopírovaný text. Pokud *počet* je větší než délka *strSource*, doplněno cílový řetězec null znaky délky *počet*. Chování **strncpy –** není definován, pokud se překrývají zdrojové a cílové řetězce.

> [!IMPORTANT]
> **strncpy –** nekontroluje dostatek místa v *strDest*; díky tomu potenciální příčinou přetečení vyrovnávací paměti. *Počet* argument omezuje počet znaků, zkopírovat, nejedná se o omezení velikosti *strDest*. Podívejte se na téma v následujícím příkladu. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).

Pokud *strDest* nebo *strSource* je **NULL** ukazatele, nebo pokud *počet* je menší než nebo rovna nule, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte **errno** k **einval –**.

**wcsncpy –** a **_mbsncpy –** jsou široká charakterová a vícebajtových znaků verze **strncpy –**. Argumenty a vrací hodnotu **wcsncpy –** a **_mbsncpy –** lišit podle toho. Tyto funkce šesti chovají stejně jako jinak.

Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají národní prostředí předaná místo aktuální národní prostředí pro jejich chování závislých na národním prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncpy –**|**strncpy**|**_mbsnbcpy**|**wcsncpy –**|
|**_tcsncpy_l –**|**_strncpy_l**|**_mbsnbcpy_l**|**_wcsncpy_l**|

> [!NOTE]
> **_strncpy_l –** a **_wcsncpy_l –** mají žádná závislost na národním prostředí, jsou k dispozici jenom pro **_tcsncpy_l –** a není určena k přímému volání.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strncpy**|\<String.h >|
|**wcsncpy –**|\<String.h > nebo \<wchar.h >|
|**_mbsncpy –**, **_mbsncpy_l –**|\<Mbstring.h >|

Informace o kompatibilitě další platformy, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje použití **strncpy –** a jak může být chybná způsobit chyby programu a problémy se zabezpečením. Kompilátor generuje upozornění pro každé volání **strncpy –** podobná **crt_strncpy_x86.c(15): upozornění C4996: 'strncpy –': Tato funkce nebo proměnná může nebezpečný. Zvažte použití strncpy_s –. Chcete-li zakázat vyřazení, použijte _CRT_SECURE_NO_WARNINGS. V nápovědě online podrobnosti.**

```C
// crt_strncpy_x86.c
// Use this command in an x86 developer command prompt to compile:
// cl /TC /W3 crt_strncpy_x86.c

#include <stdio.h>
#include <string.h>

int main() {
   char t[20];
   char s[20];
   char *p = 0, *q = 0;

   strcpy_s(s, sizeof(s), "AA BB CC");
   // Note: strncpy is deprecated; consider using strncpy_s instead
   strncpy(s, "aa", 2);     // "aa BB CC"         C4996
   strncpy(s + 3, "bb", 2); // "aa bb CC"         C4996
   strncpy(s, "ZZ", 3);     // "ZZ",              C4996
                            // count greater than strSource, null added
   printf("%s\n", s);

   strcpy_s(s, sizeof(s), "AA BB CC");
   p = strstr(s, "BB");
   q = strstr(s, "CC");
   strncpy(s, "aa", p - s - 1);   // "aa BB CC"   C4996
   strncpy(p, "bb", q - p - 1);   // "aa bb CC"   C4996
   strncpy(q, "cc",  q - s);      // "aa bb cc"   C4996
   strncpy(q, "dd", strlen(q));   // "aa bb dd"   C4996
   printf("%s\n", s);

   // some problems with strncpy
   strcpy_s(s, sizeof(s), "test");
   strncpy(t, "this is a very long string", 20 ); // C4996
   // Danger: at this point, t has no terminating null,
   // so the printf continues until it runs into one.
   // In this case, it will print "this is a very long test"
   printf("%s\n", t);

   strcpy_s(t, sizeof(t), "dogs like cats");
   printf("%s\n", t);

   strncpy(t + 10, "to chase cars.", 14); // C4996
   printf("%s\n", t);

   // strncpy has caused a buffer overrun and corrupted string s
   printf("Buffer overrun: s = '%s' (should be 'test')\n", s);
   // Since the stack grows from higher to lower addresses, buffer
   // overruns can corrupt function return addresses on the stack,
   // which can be exploited to run arbitrary code.
}
```

Výstup

```Output
ZZ
aa bb dd
this is a very long test
dogs like cats
dogs like to chase cars.
Buffer overrun: s = 'ars.' (should be 'test')
```

Rozložení automatické proměnné a úroveň ochrany, zjišťování a kód chyby se může lišit s nastavením změněné kompilátoru. V tomto příkladu může vést k odlišným výsledkům při sestavení v jiných prostředích kompilace nebo s jinými možnostmi kompilátoru.

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
