---
title: _cgets _cgetws – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _cgetws
- _cgets
apilocation:
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- cgetws
- _cgetws
- _cgets
dev_langs:
- C++
helpviewer_keywords:
- _cgetws function
- strings [C++], getting from console
- console, getting strings from
- _cgets function
- cgetws function
- cgets function
ms.assetid: 4d5e134a-58c3-4f62-befd-5d235b0212f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f30ac17204b5fc6df3ce3fe35e5c3acc98260076
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110058"
---
# <a name="cgets-cgetws"></a>_cgets, _cgetws

Získá znak řetězce z konzoly. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [_cgets_s _cgetws_s –](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
>  Tyto funkce jsou zastaralé. Od v sadě Visual Studio 2015, nejsou k dispozici v CRT. Bezpečné verze těchto funkcí, _cgets_s a _cgetws_s –, jsou stále dostupné. Informace o těchto funkcích alternativní najdete v tématu [_cgets_s _cgetws_s –](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```
char *_cgets(
   char *buffer
);
wchar_t *_cgetws(
   wchar_t *buffer
);
template <size_t size>
char *_cgets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_cgetws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro data.

## <a name="return-value"></a>Návratová hodnota

`_cgets` a `_cgetws` vrací ukazatel na začátek řetězce, na `buffer[2]`. Pokud `buffer` je **NULL**, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí **NULL** a nastavte `errno` k `EINVAL`.

## <a name="remarks"></a>Poznámky

Tyto funkce přečtou řetězec znaků z konzole a uloží řetězec a jeho délka v umístění, na které odkazuje `buffer`. `buffer` Parametr musí být ukazatel na pole znaků. První prvek pole, `buffer[0]`, musí obsahovat maximální délku (ve znacích) řetězce ke čtení. Pole musí obsahovat dostatek prvků pro uložení řetězce, ukončujícího znaku null ('\0') a dalších 2 bajtů. Funkce přečte znaky, dokud na návrat na začátek řádku return-line kanál kombinaci (CR-LF) nebo je zadaný počet znaků pro čtení. Řetězec je uložen od `buffer[2]`. Pokud funkce přečte CR-LF, uloží znak null ('\0'). Funkce potom ukládá skutečnou délku řetězce v druhém prvku pole, `buffer[1]`.

Protože všechny klávesy úprav jsou aktivní, když `_cgets` nebo `_cgetws` je volána, když v konzole okna, stisknutím klávesy F3 Zopakuje poslední zadání.

V jazyce C++ mají tyto funkce přetížení šablon, která vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablony](../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_cgets`|\<conio.h >|
|`_cgetws`|\<conio.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```
// crt_cgets.c
// compile with: /c /W3
// This program creates a buffer and initializes
// the first byte to the size of the buffer. Next, the
// program accepts an input string using _cgets and displays
// the size and text of that string.

#include <conio.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
   char buffer[83] = { 80 };  // Maximum characters in 1st byte
   char *result;

   printf( "Input line of text, followed by carriage return:\n");

   // Input a line of text:
   result = _cgets( buffer ); // C4996
   // Note: _cgets is deprecated; consider using _cgets_s
   if (!result)
   {
      printf( "An error occurred reading from the console:"
              " error code %d\n", errno);
   }
   else
   {
      printf( "\nLine length = %d\nText = %s\n",
              buffer[1], result );
   }
}
```

```Output

      A line of input.Input line of text, followed by carriage return:
Line Length = 16
Text = A line of input.
```

## <a name="see-also"></a>Viz také

[I/O konzoly a portu](../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)