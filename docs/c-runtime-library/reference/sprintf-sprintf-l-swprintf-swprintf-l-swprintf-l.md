---
title: sprintf, _sprintf_l –, swprintf –, _swprintf_l –, __swprintf_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
- ntdll.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _stprintf_l
- __swprintf_l
- sprintf_l
- swprintf
- _sprintf_l
- sprintf
- _stprintf
- stprintf_l
dev_langs:
- C++
helpviewer_keywords:
- _swprintf_l function
- _stprintf function
- __swprintf_l function
- stprintf function
- sprintf function
- _sprintf_l function
- _stprintf_l function
- swprintf function
- strings [C++], writing to
- _CRT_NON_CONFORMING_SWPRINTFS
- swprintf_l function
- stprintf_l function
- sprintf_l function
- formatted text [C++]
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02538d8c74de4f48cb4a3d6285e10c3c4e03c322
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415933"
---
# <a name="sprintf-sprintfl-swprintf-swprintfl-swprintfl"></a>sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l

Zápis formátovaná data na řetězec. Bezpečnější verze některé z těchto funkcí jsou k dispozici. v tématu [sprintf_s –, _sprintf_s_l –, swprintf_s –, _swprintf_s_l –](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md). Zabezpečené verze **swprintf –** a **_swprintf_l –** nepřebírají *počet* parametr.

## <a name="syntax"></a>Syntaxe

```C
int sprintf(
   char *buffer,
   const char *format [,
   argument] ...
);
int _sprintf_l(
   char *buffer,
   const char *format,
   locale_t locale [,
   argument] ...
);
int swprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument]...
);
int _swprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
int __swprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int sprintf(
   char (&buffer)[size],
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _sprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only

```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro výstup

*Počet*<br/>
Maximální počet znaků k uložení v kódu Unicode verze této funkce.

*Formát*<br/>
Řetězec formátu – ovládací prvek

*Argument*<br/>
Nepovinné argumenty

*Národní prostředí*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

Počet znaků, které jsou zapsány nebo -1, pokud došlo k chybě. Pokud *vyrovnávací paměti* nebo *formátu* je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte **errno** k **einval –**.

**sprintf** vrátí počet bajtů, které jsou uložené v *vyrovnávací paměti*, není počítání ukončující znak hodnoty null. **swprintf –** vrátí počet široké znaky, které jsou uložené v *vyrovnávací paměti*, není počítání ukončující široká znaková hodnotu null.

## <a name="remarks"></a>Poznámky

**Sprintf** funkce naformátuje a ukládá řady znaků a hodnot v *vyrovnávací paměti*. Každý *argument* (pokud existuje) je převeden a výstup podle odpovídající specifikaci formátu v *formátu*. Formát obsahuje obyčejnou znaky a má stejné tvoří a fungovat jako *formátu* argument pro [printf](printf-printf-l-wprintf-wprintf-l.md). Znak hodnoty null se připojí po poslední znak zapsána. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

> [!IMPORTANT]
> Pomocí **sprintf**, neexistuje žádný způsob, jak omezit počet znaků zapsána, což znamená, že programování s využitím **sprintf** náchylné k přetečení vyrovnávací paměti. Zvažte použití související funkce [_snprintf –](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), která určuje maximální počet znaků, který má být zapsána do *vyrovnávací paměti*, nebo použijte [_scprintf –](scprintf-scprintf-l-scwprintf-scwprintf-l.md) k určení jak velký vyrovnávací paměť je povinný. Také zajistěte, aby *formát* není řetězec definovaný uživatelem.

**swprintf –** je verze široká charakterová **sprintf**; ukazatel argumenty, které mají **swprintf –** jsou široká charakterová řetězce. Detekce chyb v kódování **swprintf –** se můžou lišit od v **sprintf**. **swprintf –** a **fwprintf –** vyjma toho, že se chovají stejně jako **swprintf –** zapíše výstup na řetězec, spíše než do cílového umístění v typu **souboru**a **swprintf –** vyžaduje *počet* parametru určete maximální počet znaků, který má být zapsána. Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.

**swprintf –** vyhovuje C standardu ISO, který vyžaduje parametr druhého, *počet*, typu **size_t –**. Chcete-li vynutit staré nestandardní chování, definovat **_CRT_NON_CONFORMING_SWPRINTFS**. V budoucí verzi může být odebrán staré chování, takže kódu by mělo být změněno používat nové chování vyhovující.

V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf –**|**sprintf**|**sprintf**|**_swprintf**|
|**_stprintf_l –**|**_sprintf_l**|**_sprintf_l**|**__swprintf_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**sprintf**, **_sprintf_l –**|\<stdio.h>|
|**swprintf –**, **_swprintf_l –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_sprintf.c
// compile with: /W3
// This program uses sprintf to format various
// data and place them in the string named buffer.

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996
   // Note: sprintf is deprecated; consider using sprintf_s instead

   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example"></a>Příklad

```C
// crt_swprintf.c
// wide character example
// also demonstrates swprintf returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
