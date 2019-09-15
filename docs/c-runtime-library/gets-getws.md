---
title: gets, _getws
ms.date: 11/04/2016
api_name:
- _getws
- gets
api_location:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
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
ms.openlocfilehash: 722d67336e11250f6a5459078dcea173f69bc2af
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944342"
---
# <a name="gets-_getws"></a>gets, _getws

Získá řádek z `stdin` datového proudu. K dispozici jsou bezpečnější verze těchto funkcí; viz [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
>  Tyto funkce jsou zastaralé. Počínaje verzí Visual Studio 2015 nejsou k dispozici v CRT. Zabezpečené verze těchto funkcí, gets_s a _getws_s, jsou stále k dispozici. Informace o těchto alternativních funkcích naleznete v tématu [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*vyrovnávací paměti*<br/>
Umístění úložiště pro vstupní řetězec.

## <a name="return-value"></a>Návratová hodnota

Vrátí svůj argument, pokud byl úspěšný. Ukazatel s **hodnotou null** indikuje stav chyby nebo konce souboru. K určení, která z nich se stala, použijte [trajekt](../c-runtime-library/reference/ferror.md) nebo [feof](../c-runtime-library/reference/feof.md) . Pokud `buffer` je **null**, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **hodnotu null** a nastaví errno na `EINVAL`.

## <a name="remarks"></a>Poznámky

Funkce přečte řádek ze standardního vstupního proudu `stdin` a uloží jej do `buffer`. `gets` Řádek se skládá ze všech znaků až do a včetně prvního znaku nového řádku (' \n '). `gets`před vrácením řádku nahradí znak nového řádku znakem null (' \ 0 '). Naproti tomu `fgets` funkce zachová znak nového řádku. `_getws`je verze `gets`s velkým znakem; její argument a návratová hodnota jsou řetězce s velkým počtem znaků.

> [!IMPORTANT]
>  Vzhledem k tomu, že neexistuje žádný způsob, jak omezit počet čtených znaků načtený, nedůvěryhodný vstup může snadno způsobit přetečení vyrovnávací paměti. Místo nich se používá `fgets`.

V C++nástroji mají tyto funkce přetížení šablony, které vyvolávají novější a zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablon](../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_getts`|`gets`|`gets`|`_getws`|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`gets`|\<stdio.h>|
|`_getws`|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../c-runtime-library/compatibility.md).

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

Všimněte si, že vstup delší než 20 znaků způsobí přetečení řádkové vyrovnávací paměti a téměř jistě způsobí, že se program zhroutí.

```Output

Hello there!The line entered was: Hello there!
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../c-runtime-library/stream-i-o.md)<br/>
[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)<br/>
[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)<br/>
[puts, _putws](../c-runtime-library/reference/puts-putws.md)
