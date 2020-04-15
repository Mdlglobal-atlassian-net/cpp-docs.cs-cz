---
title: gets, _getws
ms.date: 4/2/2020
api_name:
- _getws
- gets
- _o__getws
- _o_gets
api_location:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: a1fd3218f75079554d049d4ef4c3691a2fbdd542
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349324"
---
# <a name="gets-_getws"></a>gets, _getws

Získá řádek z `stdin` datového proudu. K dispozici jsou bezpečnější verze těchto funkcí. viz [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
> Tyto funkce jsou zastaralé. Počínaje Visual Studio 2015, nejsou k dispozici v CRT. Zabezpečené verze těchto funkcí, gets_s a _getws_s, jsou stále k dispozici. Informace o těchto alternativních funkcích naleznete [v tématu gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

Vrátí svůj argument, pokud je úspěšný. Ukazatel **NULL** označuje chybu nebo podmínku konce souboru. K určení, který z nich se stal, použijte [ferror](../c-runtime-library/reference/ferror.md) nebo [feof.](../c-runtime-library/reference/feof.md) Pokud `buffer` je **NULL**, tyto funkce vyvolat neplatný obslužnou rutinu parametru, jak je popsáno v [ověření parametru](../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce vrátí `EINVAL` **hodnotu NULL** a nastaví hodnotu errno na .

## <a name="remarks"></a>Poznámky

Funkce `gets` přečte řádek ze standardního vstupního datového proudu `stdin` a uloží jej do `buffer`aplikace . Řádek se skládá ze všech znaků až do prvního znaku nového řádku (\n'). `gets`před vrácením řádku nahradí znak nového řádku znakem null (\0). Naproti tomu `fgets` funkce zachová znak nového řádku. `_getws`je širokoznaková verze `gets`aplikace ; jeho argument a vrácená hodnota jsou řetězce širokých znaků.

> [!IMPORTANT]
> Vzhledem k tomu, že neexistuje žádný způsob, jak omezit počet znaků čtených získá, nedůvěryhodný vstup může snadno způsobit přetečení vyrovnávací paměti. Místo toho použijte `fgets`.

V jazyce C++ mají tyto funkce přetížení šablony, které vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace naleznete [v tématu Secure Template Overloads](../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_getts`|`gets`|`gets`|`_getws`|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`gets`|\<stdio.h>|
|`_getws`|\<stdio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```c
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

Všimněte si, že vstup delší než 20 znaků přeteče vyrovnávací paměť řádku a téměř jistě způsobí selhání programu.

```Output

Hello there!The line entered was: Hello there!
```

## <a name="see-also"></a>Viz také

[I/O proudu](../c-runtime-library/stream-i-o.md)<br/>
[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)<br/>
[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)<br/>
[puts, _putws](../c-runtime-library/reference/puts-putws.md)
