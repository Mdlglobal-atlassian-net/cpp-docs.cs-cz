---
title: scanf_s –, _scanf_s_l –, wscanf_s –, _wscanf_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 33
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96b40d891c4148a92a3d2f0060401cd84b371d73
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="scanfs-scanfsl-wscanfs-wscanfsl"></a>scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l

Čtení formátovaných dat z standardní vstupní proud. Tyto verze nástroje [scanf, _scanf_l –, wscanf, _wscanf_l –](scanf-scanf-l-wscanf-wscanf-l.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Řetězec formátu ovládacího prvku.

*Argument*<br/>
Volitelné argumenty

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí počet polí úspěšně převést a přiřazení; Návratová hodnota nezahrnuje pole, které byly pro čtení, ale není přiřazen. Vrácená hodnota 0 značí, že byly přiřazené žádné pole. Vrácená hodnota je **EOF** pro chybu, nebo pokud je zjištěn znak end souborového nebo znak ukončení řetězce v první pokus o čtení znak. Pokud *formátu* je **NULL** ukazatele, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **scanf_s –** a **wscanf_s –** vrátit **EOF** a nastavte **errno** k **einval –**.

Informace o těchto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**Scanf_s –** funkce čte data z standardní vstupní proud **stdin –** a zapisuje data do umístění, které je dán *argument*. Každý *argument* musí být ukazatel na proměnné typu, která odpovídá specifikátor typu v *formátu*. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

**wscanf_s –** je verze široká charakterová **scanf_s –**; *formátu* argument **wscanf_s –** je široká charakterová řetězec. **wscanf_s –** a **scanf_s –** chovají stejně jako datový proud se při otevření v režimu ANSI. **scanf_s –** vstup z datového proudu UNICODE aktuálně nepodporuje.

Verze tyto funkce, které mají **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí, který se předává v místo aktuální národní prostředí vlákna.

Na rozdíl od **scanf** a **wscanf**, **scanf_s –** a **wscanf_s –** vyžadují na velikost vyrovnávací paměti je možné zadat pro všechny vstupní parametry typu **c**, **C**, **s**, **S**, nebo string řízení sad, které se nacházejí v **[]**. Velikost vyrovnávací paměti ve znacích je předán jako dodatečný parametr okamžitě následující ukazatele do vyrovnávací paměti nebo proměnnou. Například pokud čtete řetězec, velikost vyrovnávací paměti pro tento řetězec je předán následujícím způsobem:

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

Velikost vyrovnávací paměti zahrnuje ukončující hodnotu null. Pole Specifikace šířky můžete zajistit, že token, který je pro čtení v se vejde do vyrovnávací paměti. Pokud se používá žádné pole Specifikace šířky a token, přečtěte si je příliš velký, aby se vešla do vyrovnávací paměti, nic se zapíše do této vyrovnávací paměti.

> [!NOTE]
> Parametr velikosti je typu **nepodepsané**, nikoli **size_t –**. Použijte statické přetypování převést **size_t –** hodnotu **nepodepsané** pro 64bitové konfigurace sestavení.

Následující příklad ukazuje, že parametr velikosti vyrovnávací paměti popisuje maximální počet znaků, ne v bajtech. Ve volání **wscanf_s –**, Šířka znaku označená typ vyrovnávací paměti neodpovídá Šířka znaku označená specifikátor formátu.

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

**S** specifikátor formátu označuje použití Šířka znaku, který je "opačným" výchozí šířku, kterou podporuje funkce. Šířka znaku je jednobajtové, ale funkce podporuje dvoubajtové znaky. Tento příklad čtení řetězec o délce až 9 znaků jedním bajty dlouhý a umístí je do vyrovnávací paměti dvojitou bajty dlouhý znak. Znaky jsou považovány za jednobajtové hodnoty; první dva znaky jsou uložené v `ws[0]`, další dva jsou uložené v `ws[1]`a tak dále.

V případě znaky může jeden znak čtení následujícím způsobem:

```C
char c;
scanf_s("%c", &c, 1);
```

Pokud se čtou více znaků, nesmí být nulová ukončenou řetězce, celá čísla používají jako specifikace šířky a velikost vyrovnávací paměti.

```C
char c[4];
scanf_s("%4c", &c, (unsigned)_countof(c)); // not null terminated
```

Další informace najdete v tématu [specifikace šířky scanf](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf_s –**|**scanf_s**|**scanf_s**|**wscanf_s**|
|**_tscanf_s_l –**|**_scanf_s_l**|**_scanf_s_l**|**_wscanf_s_l**|

Další informace najdete v tématu [pole Specifikace formátu: funkce scanf a wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**scanf_s –**, **_scanf_s_l –**|\<stdio.h>|
|**wscanf_s –**, **_wscanf_s_l –**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, **stdin –**, **stdout**, a **stderr**, musí být přesměrována C běhové funkce mohli používat v aplikacích pro UPW . Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

Tento program vytvoří následující výstup v případě, že zadané tento vstup:

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

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
