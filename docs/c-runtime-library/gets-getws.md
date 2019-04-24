---
title: gets, _getws
ms.date: 11/04/2016
apiname:
- _getws
- gets
apilocation:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getts
- gets
- _getws
helpviewer_keywords:
- getws function
- getts function
- _getws function
- lines, getting
- streams, getting lines
- _getts function
- gets function
- standard input, reading from
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
ms.openlocfilehash: bd5f4e885c0291be963320610942415fc7b61172
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62289556"
---
# <a name="gets-getws"></a>gets, _getws

Získá řádek z `stdin` datového proudu. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [gets_s – _getws_s –](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
>  Tyto funkce jsou zastaralé. Od v sadě Visual Studio 2015, nejsou k dispozici v CRT. Bezpečné verze těchto funkcí, gets_s – a _getws_s –, jsou stále dostupné. Informace o těchto funkcích alternativní najdete v tématu [gets_s – _getws_s –](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```
char *gets(
   char *buffer
);
wchar_t *_getws(
   wchar_t *buffer
);
template <size_t size>
char *gets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_getws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro vstupní řetězec.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí svůj argument. A **NULL** ukazatel myši informuje o podmínku chyby nebo end souboru. Použití [ferror](../c-runtime-library/reference/ferror.md) nebo [feof](../c-runtime-library/reference/feof.md) k určení, která z nich došlo k chybě. Pokud `buffer` je **NULL**, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **NULL** a nastaví errno na `EINVAL`.

## <a name="remarks"></a>Poznámky

`gets` Funkce přečte řádek ze standardního vstupního proudu `stdin` a uloží jej do `buffer`. Řádek obsahuje všechny znaky až včetně první znak nového řádku ('\n'). `gets` pak nahradí znak nového znaku znakem null ('\0') před vrácením řádku. Oproti tomu `fgets` funkce zachová znak nového řádku. `_getws` je širokoznaká verze `gets`; její argument a návratová hodnota jsou širokoznaké řetězce.

> [!IMPORTANT]
>  Protože neexistuje žádný způsob, jak omezit počet znaků, které jsou přečteny metodou gets, nedůvěryhodný vstup může snadno způsobit přetečení vyrovnávací paměti. Místo nich se používá `fgets`.

V jazyce C++ mají tyto funkce přetížení šablon, která vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablony](../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_getts`|`gets`|`gets`|`_getws`|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`gets`|\<stdio.h>|
|`_getws`|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```
// crt_gets.c
// compile with: /WX /W3

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets( line );  // C4996
   // Danger: No way to limit input to 20 chars.
   // Consider using gets_s instead.
   printf( "The line entered was: %s\n", line );
}
```

Všimněte si, že vstup delší než 20 znaků bude řádkové vyrovnávací paměti a téměř jistě způsobí pád programu.

```Output

Hello there!The line entered was: Hello there!
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../c-runtime-library/stream-i-o.md)<br/>
[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)<br/>
[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)<br/>
[puts, _putws](../c-runtime-library/reference/puts-putws.md)
