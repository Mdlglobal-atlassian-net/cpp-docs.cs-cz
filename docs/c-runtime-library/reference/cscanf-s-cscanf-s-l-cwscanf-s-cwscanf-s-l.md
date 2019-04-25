---
title: _cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l
ms.date: 11/04/2016
apiname:
- _cwscanf_s_l
- _cwscanf_s
- _cscanf_s
- _cscanf_s_l
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
- cscanf_s
- cscanf_s_l
- cwscanf_s
- _cwscanf_s
- _tcscanf_s
- _cscanf_s
- _cwscanf_s_l
- _cscanf_s_l
- cwscanf_s_l
- _tcscanf_s_l
- tcscanf_s
- tcscanf_s_l
helpviewer_keywords:
- cscanf_s function
- _cwscanf_s_l function
- tcscanf_s function
- console [C++], reading from
- _cscanf_s function
- data [C++], reading from the console
- cwscanf_s function
- _tcscanf_s_l function
- _cscanf_s_l function
- cscanf_s_l function
- cwscanf_s_l function
- reading data [C++], from the console
- _cwscanf_s function
- _tcscanf_s function
- tcscanf_s_l function
ms.assetid: 9ccab74d-916f-42a6-93d8-920525efdf4b
ms.openlocfilehash: b49c464c7262a60bb7744a68c0144234e152edd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288911"
---
# <a name="cscanfs-cscanfsl-cwscanfs-cwscanfsl"></a>_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l

Čtení formátovaných dat z konzoly. Tyto bezpečnější verze [_cscanf _cscanf_l –, _cwscanf – _cwscanf_l –](cscanf-cscanf-l-cwscanf-cwscanf-l.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _cscanf_s(
   const char *format [,
   argument] ...
);
int _cscanf_s_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _cwscanf_s(
   const wchar_t *format [,
   argument] ...
);
int _cwscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>Parametry

*Formát*<br/>
Řetězec řízení formátu

*argument*<br/>
Volitelné parametry.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Počet polí, které byly úspěšně převedeny a přiřazeny. Vrácená hodnota nezahrnuje pole, která byla načtena, ale nejsou přiřazena. Vrácená hodnota je **EOF** pro pokus o čtení na konci souboru. Tato situace může nastat, když je vstup z klávesnice přesměrován na úrovni příkazového řádku operačního systému. Vrácená hodnota 0 znamená, že nebyla přiřazena žádná pole.

Tyto funkce ověřují své parametry. Pokud *formátu* je ukazatel s hodnotou null, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EOF** a **errno** je nastavena na **EINVAL**.

## <a name="remarks"></a>Poznámky

**_Cscanf_s –** funkce čte data přímo z konzoly do míst daných argumentem *argument*. [_Getche](getch-getwch.md) funkce se použije ke čtení znaků. Každý volitelný parametr musí být ukazatel na proměnnou typu, který odpovídá specifikátoru typů ve *formátu*. Formát řídí interpretaci vstupních polí a má stejnou formu a funkci jako *formátu* parametr [scanf_s](scanf-scanf-l-wscanf-wscanf-l.md) funkce. Zatímco **_cscanf_s –** obvykle vrátí vstupní znak, neučiní tak pokud poslední volání bylo **_ungetch**.

Podobně jako jiné bezpečné verze funkcí v **scanf** řady **_cscanf_s –** a **_cswscanf_s** vyžadují argumenty velikosti pro znaky pole typu **c** , **C**, **s**, **S**, a **[**. Další informace najdete v tématu [specifikace šířky scanf](../../c-runtime-library/scanf-width-specification.md).

> [!NOTE]
> Velikost parametru je typu **bez znaménka**, nikoli **size_t**.

Verze těchto funkcí s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí předaného namísto aktuálního národní prostředí pro vlákno.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcscanf_s**|**_cscanf_s**|**_cscanf_s**|**_cwscanf_s**|
|**_tcscanf_s_l**|**_cscanf_s_l**|**_cscanf_s_l**|**_cwscanf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_cscanf_s**, **_cscanf_s_l**|\<conio.h>|
|**_cwscanf_s**, **_cwscanf_s_l**|\<conio.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_cscanf_s.c
// compile with: /c
/* This program prompts for a string
* and uses _cscanf_s to read in the response.
* Then _cscanf_s returns the number of items
* matched, and the program displays that number.
*/

#include <stdio.h>
#include <conio.h>

int main( void )
{
   int result, n[3];
   int i;

   result = _cscanf_s( "%i %i %i", &n[0], &n[1], &n[2] );
   _cprintf_s( "\r\nYou entered " );
   for( i=0; i<result; i++ )
      _cprintf_s( "%i ", n[i] );
   _cprintf_s( "\r\n" );
}
```

```Input
1 2 3
```

```Output
You entered 1 2 3
```

## <a name="see-also"></a>Viz také:

[I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
