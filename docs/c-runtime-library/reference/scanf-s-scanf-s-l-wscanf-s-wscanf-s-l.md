---
title: scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l
ms.date: 03/26/2019
apiname:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
ms.openlocfilehash: 28697cac20181c3dda0581c7486ebb673aec1241
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508799"
---
# <a name="scanfs-scanfsl-wscanfs-wscanfsl"></a>scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l

Čtení formátovaných dat ze standardního vstupního proudu. Tyto verze [scanf _scanf_l –, wscanf _wscanf_l –](scanf-scanf-l-wscanf-wscanf-l.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Formát*<br/>
Řetězec řízení formátu.

*argument*<br/>
Volitelné argumenty

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí počet polí úspěšně převedena a přidělena. Vrácená hodnota nezahrnuje pole, která byla načtena, ale nejsou přiřazena. Vrácená hodnota 0 označuje, že nebyla přiřazena žádná pole. Vrácená hodnota je **EOF** pro chybu, nebo pokud se najde endovém souborovém znak nebo znak ukončení řetězce při prvním pokusu o čtení znaku. Pokud *formátu* je **NULL** vyvolána ukazatel, obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **scanf_s** a **wscanf_s –** vrátit **EOF** a nastavte **errno** k **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**Scanf_s** funkce přečte data ze standardního vstupního proudu **stdin**a zapíše jej do *argument*. Každý *argument* musí být ukazatel na typ proměnné, který odpovídá specifikátoru typů ve *formátu*. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

**wscanf_s –** je verze širokého znaku **scanf_s**; *formátu* argument **wscanf_s –** je širokoznaký řetězec. **wscanf_s –** a **scanf_s** chovají stejně jako v případě, že datový proud je otevřen v režimu ANSI. **scanf_s** aktuálně nepodporuje vstup z datového proudu UNICODE.

Verze těchto funkcí, které mají **_l** přípona jsou identické, s tím rozdílem, že používají *národní prostředí* parametr namísto aktuálního národní prostředí pro vlákno.

Na rozdíl od **scanf** a **wscanf**, **scanf_s** a **wscanf_s –** vyžadují zadání velikosti vyrovnávací paměti pro některé parametry. Zadejte pro všechny velikosti **c**, **C**, **s**, **S**, nebo řetězec sada ovládacích prvků **[]** parametry. Velikost vyrovnávací paměti ve znacích je předána jako další parametr. Bezprostředně následuje ukazatel do vyrovnávací paměti nebo proměnné. Například pokud čtete řetězec, velikost vyrovnávací paměti pro tento řetězec je předán následujícím způsobem:

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

Vyrovnávací paměť obsahuje terminálu hodnotu null. Pole pro specifikaci šířky můžete použít k zajištění token, který je určen pro čtení přizpůsobí do vyrovnávací paměti. Když token je příliš velká, nic se zapíše do vyrovnávací paměti není specifikace šířky.

> [!NOTE]
> Velikost parametru je typu **bez znaménka**, nikoli **size_t**. Použijte statické přetypování pro převod **size_t** hodnota, která se **bez znaménka** pro 64bitovou verzi konfigurace sestavení.

Parametr velikosti vyrovnávací paměti popisuje maximální počet znaků, ne v bajtech. V tomto příkladu šířka vyrovnávací paměti typu neodpovídá šířka specifikátor formátu.

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

**S** specifikátor formátu znamená, že šířka znaku, který je "u" Výchozí šířka nepodporuje funkci používat. Šířka znaku je jeden bajt, ale funkce podporuje dvoubajtové znaky. Tento příklad přečte v řetězec o délce maximálně devět jeden bajt celou znaků a umístí je do vyrovnávací paměti double byte širokého znaku. Znaky jsou považovány za hodnoty jednobajtové; první dva znaky jsou uloženy v `ws[0]`, další dva, jsou uloženy v `ws[1]`, a tak dále.

Tento příklad načte jeden znak:

```C
char c;
scanf_s("%c", &c, 1);
```

Při čtení více znaků pro jiné-řetězec zakončený null celých čísel se používají pro specifikaci šířky a velikost vyrovnávací paměti.

```C
char c[4];
scanf_s("%4c", c, (unsigned)_countof(c)); // not null terminated
```

Další informace najdete v tématu [specifikace šířky scanf](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf_s**|**scanf_s**|**scanf_s**|**wscanf_s**|
|**_tscanf_s_l**|**_scanf_s_l**|**_scanf_s_l**|**_wscanf_s_l**|

Další informace najdete v tématu [pole Specifikace formátu: funkce scanf a wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**scanf_s**, **_scanf_s_l**|\<stdio.h>|
|**wscanf_s**, **_wscanf_s_l**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UPW). Standardní datový proud popisovačů **stdin**, **stdout**, a **stderr** musí být přesměrován před funkcí jazyka C za běhu můžete použít v aplikacích pro UPW. Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

Tento program vytvoří následující výstup, když tento vstup:

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
[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
