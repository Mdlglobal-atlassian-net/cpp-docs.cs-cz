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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: afffb691ca8bf8d180cac11ac5f16a84d871b1b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334418"
---
# <a name="_cgets-_cgetws"></a>_cgets, _cgetws

Získá řetězec znaku z konzoly. K dispozici jsou bezpečnější verze těchto funkcí. viz [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
> Tyto funkce jsou zastaralé. Počínaje Visual Studio 2015, nejsou k dispozici v CRT. Zabezpečené verze těchto funkcí, _cgets_s a _cgetws_s, jsou stále k dispozici. Informace o těchto alternativních funkcích naleznete [v tématu _cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

`_cgets`a `_cgetws` vrátí ukazatel na začátek řetězce, at `buffer[2]`. Pokud `buffer` je **NULL**, tyto funkce vyvolat neplatný obslužnou rutinu parametru, jak je popsáno v [ověření parametru](../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, vrátí `errno` `EINVAL` **hodnotu NULL** a je nastavena na hodnotu .

## <a name="remarks"></a>Poznámky

Tyto funkce číst řetězec znaků z konzoly a uložit řetězec a `buffer`jeho délku v umístění, na které se vztahuje . Parametr `buffer` musí být ukazatel na pole znaků. První prvek pole , `buffer[0]`musí obsahovat maximální délku (ve znacích) řetězce, který má být přečten. Pole musí obsahovat dostatek prvků pro uložení řetězce, ukončující znak null (\0) a 2 další bajty. Funkce čte znaky, dokud není přečtena kombinace zpětného kanálu řádku vozíku (CR-LF) nebo zadaný počet znaků. Řetězec je uložen `buffer[2]`od . Pokud funkce přečte CR-LF, uloží prázdný znak (\0).If the function reads a CR-LF, it stores the null character ('\0'). Funkce pak ukládá skutečnou délku řetězce v `buffer[1]`druhém prvku pole .

Vzhledem k tomu, `_cgets` že `_cgetws` všechny klávesy pro úpravy jsou aktivní, když nebo je volána v okně konzoly, stisknutím klávesy F3 se opakuje poslední zadaná položka.

V jazyce C++ mají tyto funkce přetížení šablony, které vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace naleznete [v tématu Secure Template Overloads](../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_cgets`|\<conio.h>|
|`_cgetws`|\<conio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../c-runtime-library/compatibility.md).

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
