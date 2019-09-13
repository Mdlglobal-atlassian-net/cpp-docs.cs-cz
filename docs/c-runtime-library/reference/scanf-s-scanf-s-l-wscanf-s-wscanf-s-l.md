---
title: scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l
ms.date: 03/26/2019
api_name:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wscanf_s
- _tscanf_s_l
- _wscanf_s_l
- scanf_s
- _tscanf_s
- _scanf_s_l
helpviewer_keywords:
- reading data [C++], from input streams
- buffers [C++], buffer overruns
- _scanf_s_l function
- _wscanf_s_l function
- tscanf_s_l function
- tscanf_s function
- scanf_s function
- data [C++], reading from input stream
- wscanf_s function
- _tscanf_s_l function
- _tscanf_s function
- scanf_s_l function
- formatted data [C++], from input streams
- wscanf_s_l function
- buffers [C++], avoiding overruns
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
ms.openlocfilehash: e869f9e0d4fa87c87878ffea987e4b6d85a75616
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948878"
---
# <a name="scanf_s-_scanf_s_l-wscanf_s-_wscanf_s_l"></a>scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l

Přečte formátovaná data ze standardního vstupního datového proudu. Tyto verze [scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int scanf_s(
   const char *format [,
   argument]...
);
int _scanf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf_s(
   const wchar_t *format [,
   argument]...
);
int _wscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Parametry

*format*<br/>
Formátovací řetězec ovládacího prvku

*argument*<br/>
Volitelné argumenty

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí počet úspěšně převedených a přiřazených polí. Vrácená hodnota nezahrnuje pole, která byla načtena, ale nebyla přiřazena. Návratová hodnota 0 značí, že nebyla přiřazena žádná pole. Návratová hodnota je znak **EOF** pro chybu, nebo pokud se při prvním pokusu o čtení znaku najde znak konce souboru nebo znak konce řetězce. Pokud je *Format* ukazatel s **hodnotou null** , je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **scanf_s** a **wscanf_s** vrátí **EOF** a nastaví **errno** na **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **scanf_s** čte data ze standardního vstupního streamu, **stdin**a zapisuje je do *argumentu*. Každý *argument* musí být ukazatel na typ proměnné, který odpovídá specifikátoru typu ve *formátu*. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

**wscanf_s** je **scanf_s**verze s velkým znakem; Argument *Format* pro **wscanf_s** je řetězec s velkým znakem. **wscanf_s** a **scanf_s** se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **scanf_s** v současné době nepodporuje vstup z datového proudu Unicode.

Verze těchto funkcí, které mají příponu **_l** , jsou identické, s výjimkou použití parametru *locale* namísto aktuálního národního prostředí vlákna.

Na rozdíl od **scanf** a **wscanf**, **scanf_s** a **wscanf_s** vyžadují, abyste pro některé parametry zadali velikost vyrovnávací paměti. Zadejte velikosti pro všechny parametry **c**, **c**, **s**, **s**nebo sada ovládacího prvku řetězce **[]** . Velikost vyrovnávací paměti ve znacích se předává jako další parametr. Hned následuje ukazatel na vyrovnávací paměť nebo proměnnou. Například při čtení řetězce je velikost vyrovnávací paměti tohoto řetězce předána následujícím způsobem:

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

Velikost vyrovnávací paměti zahrnuje hodnotu Terminal null. Pole Specifikace šířky můžete použít k zajištění toho, aby token, který je čten do vyrovnávací paměti, odpovídal. Pokud je token moc velký, aby se vešel, do vyrovnávací paměti se nic nezapisuje, pokud neexistuje specifikace šířky.

> [!NOTE]
> Parametr size je typu **bez znaménka**, nikoli **size_t**. Použijte statické přetypování pro převod hodnoty **size_t** na **unsigned** pro 64 konfigurace sestavení.

Parametr velikosti vyrovnávací paměti popisuje maximální počet znaků, nikoli bajtů. V tomto příkladu šířka typu vyrovnávací paměti neodpovídá šířce specifikátoru formátu.

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

Specifikátor formátu **S** znamená, že se jako výchozí šířka podporovaná funkcí používá Šířka znaku, která je "opak". Šířka znaku je jeden bajt, ale funkce podporuje dvoubajtové znaky. Tento příklad přečte v řetězci až devět znaků v jednom bajtu a umístí je do vyrovnávací paměti pro dvoubajtové znaky. Znaky jsou považovány za jednobajtové hodnoty; první dva znaky jsou uloženy v `ws[0]`, druhý dva jsou uloženy v `ws[1]`a tak dále.

Tento příklad přečte jeden znak:

```C
char c;
scanf_s("%c", &c, 1);
```

Je-li čteno více znaků pro řetězce, které nejsou zakončeny hodnotou null, jsou celá čísla použita pro specifikaci šířky i pro velikost vyrovnávací paměti.

```C
char c[4];
scanf_s("%4c", c, (unsigned)_countof(c)); // not null terminated
```

Další informace najdete v tématu [specifikace šířky scanf](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf_s**|**scanf_s**|**scanf_s**|**wscanf_s**|
|**_tscanf_s_l**|**_scanf_s_l**|**_scanf_s_l**|**_wscanf_s_l**|

Další informace najdete v tématu [formátování pole Specifikace: scanf a wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**scanf_s**, **_scanf_s_l**|\<stdio.h>|
|**wscanf_s**, **_wscanf_s_l**|\<stdio. h > nebo \<WCHAR. h >|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní datový proud zpracovává funkce **stdin**, **stdout**a **stderr** , aby je bylo možné použít v aplikacích pro UWP a za běhu. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_scanf_s.c
// This program uses the scanf_s and wscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int      i,
            result;
   float    fp;
   char     c,
            s[80];
   wchar_t  wc,
            ws[80];

   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,
           wc, s, ws);
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,
            c, wc, s, ws);
}
```

Tento program při zadání tohoto vstupu vygeneruje následující výstup:

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
