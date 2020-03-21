---
title: _cscanf, _cscanf_l, _cwscanf, _cwscanf_l
ms.date: 10/21/2019
api_name:
- _cscanf_l
- _cscanf
- _cwscanf
- _cwscanf_l
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cwscanf
- cwscanf_l
- tcscanf_l
- _tcscanf_l
- _cscanf
- _cscanf_l
- tcscanf
- cwscanf
- _cwscanf_l
- cscanf_l
- _tcscanf
helpviewer_keywords:
- _cwscanf function
- data [C++], reading from the console
- cscanf_l function
- tcscanf function
- _cscanf_l function
- cwscanf function
- _tcscanf_l function
- _cscanf function
- _tcscanf function
- cwscanf_l function
- tcscanf_l function
- reading data [C++], from the console
- _cwscanf_l function
ms.assetid: dbfe7547-b577-4567-a1cb-893fa640e669
ms.openlocfilehash: 973642aa113c8db4174b399f22e980daba95ce41
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079986"
---
# <a name="_cscanf-_cscanf_l-_cwscanf-_cwscanf_l"></a>_cscanf, _cscanf_l, _cwscanf, _cwscanf_l

Přečte formátovaná data z konzoly. K dispozici jsou bezpečnější verze těchto funkcí; viz [_cscanf_s, _cscanf_s_l, _cwscanf_s _cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md).

> [!NOTE]
> V aplikaci Visual Studio 2015 `printf` a `scanf` rodina funkcí byly deklarovány jako **inline** a přesunuty do hlaviček `<stdio.h>` a `<conio.h>`. Pokud migrujete starší kód, může se v souvislosti s těmito funkcemi zobrazit *linkerů LNK2019* . Další informace najdete v tématu [o C++ historii vizuálních změn 2003 – 2015](../../porting/visual-cpp-change-history-2003-2015.md#stdio_and_conio).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _cscanf(
   const char *format [,
   argument] ...
);
int _cscanf_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _cwscanf(
   const wchar_t *format [,
   argument] ...
);
int _cwscanf_l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>Parametry

*formátovat*<br/>
Řetězec řízení formátu

*Argument*<br/>
Volitelné parametry.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Počet polí, která byla úspěšně převedena a přiřazena. Vrácená hodnota nezahrnuje pole, která byla načtena, ale nebyla přiřazena. Návratová hodnota je znak **EOF** pro pokus o čtení na konci souboru. Tato situace může nastat, pokud je vstup z klávesnice přesměrován na úrovni příkazového řádku operačního systému. Návratová hodnota 0 znamená, že nebyla přiřazena žádná pole.

## <a name="remarks"></a>Poznámky

Funkce **_cscanf** čte data přímo z konzoly do umístění předaných *argumentem*. Funkce [_getche](getch-getwch.md) slouží ke čtení znaků. Každý volitelný parametr musí být ukazatel na proměnnou s typem, který odpovídá specifikátoru typu ve *formátu*. Formát řídí interpretaci vstupních polí a má stejnou formu a funkci jako parametr *Format* pro funkci [scanf](scanf-scanf-l-wscanf-wscanf-l.md) . Zatímco **_cscanf** obvykle vypisuje vstupní znak, neudělá to, pokud poslední volání bylo **_ungetch**.

Tato funkce ověří své parametry. Pokud má formát **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **EOF**.

Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí vlákna.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcscanf**|**_cscanf**|**_cscanf**|**_cwscanf**|
|**_tcscanf_l**|**_cscanf_l**|**_cscanf_l**|**_cwscanf_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_cscanf** **_cscanf_l**|\<CONIO. h >|
|**_cwscanf** **_cwscanf_l**|\<CONIO. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_cscanf.c
// compile with: /c /W3
/* This program prompts for a string
* and uses _cscanf to read in the response.
* Then _cscanf returns the number of items
* matched, and the program displays that number.
*/

#include <stdio.h>
#include <conio.h>

int main( void )
{
   int   result, i[3];

   _cprintf_s( "Enter three integers: ");
   result = _cscanf( "%i %i %i", &i[0], &i[1], &i[2] ); // C4996
   // Note: _cscanf is deprecated; consider using _cscanf_s instead
   _cprintf_s( "\r\nYou entered " );
   while( result-- )
      _cprintf_s( "%i ", i[result] );
   _cprintf_s( "\r\n" );
}
```

```Input
1 2 3
```

```Output
Enter three integers: 1 2 3
You entered 3 2 1
```

## <a name="see-also"></a>Viz také

[I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
