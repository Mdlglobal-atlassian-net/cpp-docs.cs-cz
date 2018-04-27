---
title: sscanf_s –, _sscanf_s_l –, swscanf_s –, _swscanf_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- _stscanf_s
- sscanf_s
- swscanf_s
- _swscanf_s_l
- _stscanf_s_l
- _sscanf_s_l
dev_langs:
- C++
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
caps.latest.revision: 30
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 995cf583751903527fec9518b81b4048844d4f52
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="sscanfs-sscanfsl-swscanfs-swscanfsl"></a>sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l

Čtení formátovaných dat z řetězce. Tyto verze nástroje [sscanf –, _sscanf_l –, swscanf –, _swscanf_l –](sscanf-sscanf-l-swscanf-swscanf-l.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Argument*<br/>
Nepovinné argumenty

*Národní prostředí*<br/>
Národní prostředí používat

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí počet polí, které jsou úspěšně převést a přiřadit; Návratová hodnota nezahrnuje pole, které byly pro čtení, ale není přiřazen. Vrácená hodnota 0 značí, že byly přiřazené žádné pole. Vrácená hodnota je **EOF** pro chybu nebo pokud je dosaženo konce řetězec před první převod.

Pokud *vyrovnávací paměti* nebo *formátu* je **NULL** ukazatele, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte **errno** k **einval –**

Informace o těchto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**Sscanf_s –** funkce Číst data z *vyrovnávací paměti* do umístění, který je přiřazen každou *argument*. Ukazatelé na proměnné, které mají typ, který odpovídá specifikátor typu v zadejte argumenty po řetězec formátu *formátu*. Na rozdíl od méně bezpečná verze [sscanf –](sscanf-sscanf-l-swscanf-swscanf-l.md), parametr velikost vyrovnávací paměti je povinný při použití znaky pole typu **c**, **C**, **s**, **S**, nebo string řízení sad, které se nacházejí v **[]**. Velikost vyrovnávací paměti ve znacích je nutné zadat jako dodatečný parametr ihned po každé parametr vyrovnávací paměti, který vyžaduje. Například pokud čtete na řetězec, velikost vyrovnávací paměti pro tento řetězec je předán následujícím způsobem:

```C
wchar_t ws[10];
swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9
```

Velikost vyrovnávací paměti zahrnuje ukončující hodnotu null. Pole Specifikace šířky lze zajistit, že token, který je pro čtení v se vejde do vyrovnávací paměti. Pokud se používá žádné pole Specifikace šířky a token, přečtěte si je příliš velký, aby se vešla do vyrovnávací paměti, nic se zapíše do této vyrovnávací paměti.

V případě znaky může jeden znak čtení následujícím způsobem:

```C
wchar_t wc;
swscanf_s(in_str, L"%c", &wc, 1);
```

Tento příklad čte jeden znak z vstupní řetězec a ukládá je do vyrovnávací paměti široká charakterová. Při čtení více znaků, nesmí být nulová ukončenou řetězce znaménka slouží jako specifikace šířky a velikost vyrovnávací paměti.

```C
char c[4];
sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated
```

Další informace najdete v tématu [scanf_s –, _scanf_s_l –, wscanf_s –, _wscanf_s_l –](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) a [znaky pole typu scanf](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Parametr velikosti je typu **nepodepsané**, nikoli **size_t –**. Při kompilaci pro 64bitové verze cíle, použijte statické přetypování převést **_countof –** nebo **sizeof** výsledky správnou velikost.

*Formátu* ovládací prvky argument výklad vstupní pole a má stejnou tvoří a fungovat jako *formátu* argument **scanf_s –** funkce. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

**swscanf_s –** je verze široká charakterová **sscanf_s –**; argumenty, které mají **swscanf_s –** jsou široká charakterová řetězce. **sscanf_s –** nezpracovává vícebajtové hexadecimálních znaků. **swscanf_s –** nezpracovává šestnáctkové kódování Unicode s plnou šířkou nebo znaků "kompatibility zóna". V opačném **swscanf_s –** a **sscanf_s –** chovají stejně jako.

Verze tyto funkce, které mají **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí, který se předává v místo aktuální národní prostředí vlákna.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf_s –**|**sscanf_s**|**sscanf_s**|**swscanf_s**|
|**_stscanf_s_l –**|**_sscanf_s_l**|**_sscanf_s_l**|**_swscanf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**sscanf_s –**, **_sscanf_s_l –**|\<stdio.h>|
|**swscanf_s –**, **_swscanf_s_l –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
   // max 80 character string plus NULL terminator
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

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
