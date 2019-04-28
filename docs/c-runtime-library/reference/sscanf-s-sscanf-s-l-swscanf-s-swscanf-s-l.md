---
title: sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l
ms.date: 11/04/2016
apiname:
- _sscanf_s_l
- sscanf_s
- _swscanf_s_l
- swscanf_s
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _stscanf_s
- sscanf_s
- swscanf_s
- _swscanf_s_l
- _stscanf_s_l
- _sscanf_s_l
helpviewer_keywords:
- stscanf_s_l function
- stscanf_s function
- swscanf_s function
- swscanf_s_l function
- sscanf_s_l function
- _stscanf_s_l function
- strings [C++], reading data from
- sscanf_s function
- _swscanf_s_l function
- _stscanf_s function
- reading data, strings
- strings [C++], reading
- _sscanf_s_l function
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
ms.openlocfilehash: 07911b7254e74c28310669a697c7492b69567b7f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62354794"
---
# <a name="sscanfs-sscanfsl-swscanfs-swscanfsl"></a>sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l

Čtení formátovaných dat z řetězce. Tyto verze [sscanf – _sscanf_l –, swscanf – _swscanf_l –](sscanf-sscanf-l-swscanf-swscanf-l.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int sscanf_s(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_s_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf_s(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_s_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Uložená data

*Formát*<br/>
Řetězec řízení formátu Další informace najdete v tématu [pole Specifikace formátu: funkce scanf a wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*argument*<br/>
Nepovinné argumenty.

*Národní prostředí*<br/>
Národní prostředí

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí počet polí, která jsou úspěšně převedena a přidělena; Vrácená hodnota nezahrnuje pole, která byla načtena, ale nejsou přiřazena. Vrácená hodnota 0 označuje, že nebyla přiřazena žádná pole. Vrácená hodnota je **EOF** pro chybu nebo pokud je dosaženo konce řetězce před prvním převodem.

Pokud *vyrovnávací paměti* nebo *formátu* je **NULL** vyvolána ukazatel, obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EINVAL**

Informace o těchto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**Sscanf_s –** funkce načítá data z *vyrovnávací paměti* do umístění, která je přidělena každou *argument*. Argumenty za formátovacím řetězci určují odkazy na proměnné, které mají typ, který odpovídá specifikátoru typů ve *formátu*. Na rozdíl od méně bezpečné verze [sscanf –](sscanf-sscanf-l-swscanf-swscanf-l.md), parametr velikosti vyrovnávací paměti je povinný, pokud používáte znaky pole typu **c**, **C**, **s**, **S**, nebo sad řízení, které jsou uzavřeny v řetězců **[]**. Velikost vyrovnávací paměti ve znacích musí být dodána jako další parametr ihned po každého parametru mezipaměti, který jej vyžaduje. Například pokud načítáte do řetězce, velikost vyrovnávací paměti pro tento řetězec je předán následujícím způsobem:

```C
wchar_t ws[10];
swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9
```

Vyrovnávací paměť obsahuje ukončující znak null. Pole pro specifikaci šířky slouží k zajištění, že token, který je určen pro čtení, se vejde do vyrovnávací paměti. Pokud žádná pole pro specifikaci šířky a čtený token je nevejdou do vyrovnávací paměti, není nic zapsáno do vyrovnávací paměti.

V případě znaků jeden znak může být trochu odlišná:

```C
wchar_t wc;
swscanf_s(in_str, L"%c", &wc, 1);
```

Tento příklad přečte znak ze vstupního řetězce a pak je uloží do vyrovnávací paměti širokého znaku. Při čtení více znaků řetězců ukončených nenulovou celých čísel bez znaménka se používají jako specifikace šířky a velikost vyrovnávací paměti.

```C
char c[4];
sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated
```

Další informace najdete v tématu [scanf_s _scanf_s_l –, wscanf_s – _wscanf_s_l –](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) a [scanf – znaky pole typu](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Velikost parametru je typu **bez znaménka**, nikoli **size_t**. Při kompilaci pro 64bitové cíle, použijte statické přetypování pro převod **_countof** nebo **sizeof** výsledky na správnou velikost.

*Formátu* argument řídí interpretaci vstupních polí a má stejnou formu a funkci jako *formátu* argument **scanf_s** funkce. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

**swscanf_s –** je verze širokého znaku **sscanf_s –**; argumenty, které mají **swscanf_s –** jsou širokoznaké řetězce. **sscanf_s –** nezpracovává vícebajtové znaky v šestnáctkové soustavě. **swscanf_s –** nezpracovává šestnáctkové kódování Unicode s plnou šířkou nebo znaky "oblasti kompatibility". V opačném případě **swscanf_s –** a **sscanf_s –** chovají identicky.

Verze těchto funkcí, které mají **_l** přípona jsou stejné s tím rozdílem, že používají Předaný parametr národního prostředí namísto aktuálního národní prostředí pro vlákno.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf_s**|**sscanf_s**|**sscanf_s**|**swscanf_s**|
|**_stscanf_s_l**|**_sscanf_s_l**|**_sscanf_s_l**|**_swscanf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**sscanf_s**, **_sscanf_s_l**|\<stdio.h>|
|**swscanf_s**, **_swscanf_s_l**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_sscanf_s.c
// This program uses sscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string plus null terminator
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );
   sscanf_s( tokenstring, "%d", &i );
   sscanf_s( tokenstring, "%f", &fp );

   // Output the data read
   printf_s( "String    = %s\n", s );
   printf_s( "Character = %c\n", c );
   printf_s( "Integer:  = %d\n", i );
   printf_s( "Real:     = %f\n", fp );
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
