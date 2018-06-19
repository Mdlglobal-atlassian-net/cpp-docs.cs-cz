---
title: fscanf_s –, _fscanf_s_l –, fwscanf_s –, _fwscanf_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fwscanf_s
- _fscanf_s_l
- _fwscanf_s_l
- fscanf_s
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
- _fwscanf_s_l
- _fscanf_s_l
- fscanf_s
- _ftscanf_s_l
- _ftscanf_s
- fwscanf_s
dev_langs:
- C++
helpviewer_keywords:
- formatted data [C++], reading from streams
- _ftscanf_s_l function
- _fscanf_s_l function
- ftscanf_s function
- fwscanf_s function
- _ftscanf_s function
- data [CRT], reading from streams
- _fwscanf_s_l function
- fscanf_s function
- fwscanf_s_l function
- ftscanf_s_l function
- streams [C++], reading formatted data from
- fscanf_s_l function
ms.assetid: b6e88194-714b-4322-be82-1cc0b343fe01
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62bca0d0d53871e507ce47eb878fed663443bd40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405377"
---
# <a name="fscanfs-fscanfsl-fwscanfs-fwscanfsl"></a>fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l

Čtení formátovaných dat z datového proudu. Tyto verze nástroje [fscanf –, _fscanf_l –, fwscanf –, _fwscanf_l –](fscanf-fscanf-l-fwscanf-fwscanf-l.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int fscanf_s(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fscanf_s_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int fwscanf_s(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwscanf_s_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>Parametry

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

*Formát*<br/>
Řetězec řízení formátu

*Argument*<br/>
Volitelné argumenty

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí počet polí, které jsou úspěšně převést a přiřadit; Návratová hodnota nezahrnuje pole, které byly pro čtení, ale není přiřazen. Vrácená hodnota 0 značí, že byly přiřazené žádné pole. Pokud dojde k chybě, nebo pokud je dosaženo konce datový proud souboru před prvním převodu, je vrácenou hodnotu **EOF** pro **fscanf_s –** a **fwscanf_s –**.

Tyto funkce ověřit jejich parametrů. Pokud *datového proudu* je ukazatel souboru je neplatný, nebo *formátu* je ukazatel s hodnotou null, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **EOF** a nastavte **errno** k **einval –**.

## <a name="remarks"></a>Poznámky

**Fscanf_s –** funkce čte data z aktuální pozici *datového proudu* do umístění, která platí při *argument* (pokud existuje). Každý *argument* musí být ukazatel na proměnné typu, která odpovídá specifikátor typu v *formátu*. *Formát* ovládací prvky výklad vstupní pole a má stejnou tvoří a fungovat jako *formátu* argument pro **scanf_s –**; najdete v části [pole Specifikace formátu: Funkce scanf a wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md) popis *formátu*.  **fwscanf_s –** je verze široká charakterová **fscanf_s –**; argument formátu **fwscanf_s –** je široká charakterová řetězec. Tyto funkce chovají stejně jako datový proud se při otevření v režimu ANSI. **fscanf_s –** vstup z datového proudu UNICODE aktuálně nepodporuje.

Hlavní rozdíl mezi bezpečnější funkce (které mají **_Malá** příponu) a jiné verze je, že bezpečnější funkce vyžadovat velikosti ve znacích jednotlivých **c**, **C**, **s**, **S**, a **[** typ pole, které chcete předat jako argument okamžitě následující proměnné. Další informace najdete v tématu [scanf_s –, _scanf_s_l –, wscanf_s –, _wscanf_s_l –](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) a [specifikace šířky scanf](../../c-runtime-library/scanf-width-specification.md).

> [!NOTE]
> Parametr velikosti je typu **nepodepsané**, nikoli **size_t –**.

Verze tyto funkce, které mají **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí, který se předává v místo aktuální národní prostředí vlákna.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftscanf_s –**|**fscanf_s**|**fscanf_s**|**fwscanf_s**|
|**_ftscanf_s_l –**|**_fscanf_s_l**|**_fscanf_s_l**|**_fwscanf_s_l**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fscanf_s –**, **_fscanf_s_l –**|\<stdio.h>|
|**fwscanf_s –**, **_fwscanf_s_l –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fscanf_s.c
// This program writes formatted
// data to a file. It then uses fscanf to
// read the various data back from the file.

#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   long l;
   float fp;
   char s[81];
   char c;

   errno_t err = fopen_s( &stream, "fscanf.out", "w+" );
   if( err )
      printf_s( "The file fscanf.out was not opened\n" );
   else
   {
      fprintf_s( stream, "%s %ld %f%c", "a-string",
               65000, 3.14159, 'x' );
      // Set pointer to beginning of file:
      fseek( stream, 0L, SEEK_SET );

      // Read data back from file:
      fscanf_s( stream, "%s", s, _countof(s) );
      fscanf_s( stream, "%ld", &l );

      fscanf_s( stream, "%f", &fp );
      fscanf_s( stream, "%c", &c, 1 );

      // Output data read:
      printf( "%s\n", s );
      printf( "%ld\n", l );
      printf( "%f\n", fp );
      printf( "%c\n", c );

      fclose( stream );
   }
}
```

```Output
a-string
65000
3.141590
x
```

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
