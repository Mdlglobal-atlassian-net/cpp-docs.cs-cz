---
title: _cgets, _cgetws
ms.date: 4/2/2020
api_name:
- _cgetws
- _cgets
- _o__cgets
- _o__cgetws
api_location:
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-conio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cgetws
- _cgetws
- _cgets
helpviewer_keywords:
- _cgetws function
- strings [C++], getting from console
- console, getting strings from
- _cgets function
- cgetws function
- cgets function
ms.assetid: 4d5e134a-58c3-4f62-befd-5d235b0212f4
ms.openlocfilehash: 9ae7baaa01029dcf2c02f6ea80b6e816bb671596
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917432"
---
# <a name="_cgets-_cgetws"></a>_cgets, _cgetws

Získá řetězec znaků z konzoly. K dispozici jsou bezpečnější verze těchto funkcí; viz [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
> Tyto funkce jsou zastaralé. Počínaje verzí Visual Studio 2015 nejsou k dispozici v CRT. Zabezpečené verze těchto funkcí, _cgets_s a _cgetws_s, jsou stále k dispozici. Informace o těchto alternativních funkcích naleznete v tématu [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*vyrovnávací paměti*<br/>
Umístění úložiště pro data

## <a name="return-value"></a>Návratová hodnota

`_cgets`a `_cgetws` vrátí ukazatel na začátek řetězce, v `buffer[2]`. Pokud `buffer` je **null**, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí **hodnotu null** a nastaví `errno` na `EINVAL`.

## <a name="remarks"></a>Poznámky

Tyto funkce čtou řetězec znaků z konzoly a uloží řetězec a jeho délku do umístění, na které ukazuje `buffer`. `buffer` Parametr musí být ukazatel na pole znaků. První prvek pole, `buffer[0]`, musí obsahovat maximální délku (ve znacích) řetězce, který se má přečíst. Pole musí obsahovat dostatek prvků pro uložení řetězce, ukončujícího znaku null (' \ 0 ') a dalších 2 bajtů. Funkce přečte znaky, dokud není přečtena kombinace datového kanálu návratového řádku (CR-LF) nebo zadaného počtu znaků. Řetězec je uložen od `buffer[2]`. Pokud funkce přečte CR-LF, uloží znak null (' \ 0 '). Funkce pak uloží skutečnou délku řetězce v druhém prvku pole, `buffer[1]`.

Vzhledem k tomu, že jsou všechny `_cgets` editační `_cgetws` klíče aktivní, když je v okně konzoly volána nebo, klávesa F3 opakuje poslední zadanou položku.

V jazyce C++ mají tyto funkce přetížení šablony, které vyvolávají novější a zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablon](../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_cgets`|\<CONIO. h>|
|`_cgetws`|\<CONIO. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```c
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
