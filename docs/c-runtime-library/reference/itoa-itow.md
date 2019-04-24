---
title: _itoa – _itow – funkce
ms.date: 03/21/2018
apiname:
- itoa
- _itoa
- ltoa
- _ltoa
- ultoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _itoa
- _ltoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- itoa
- ltoa
- ultoa
- i64toa
- ui64toa
- itow
- ltow
- ultow
- i64tow
- ui64tow
- itot
- _itot
- ltot
- _ltot
- ultot
- _ultot
- i64tot
- _i64tot
- ui64tot
- _ui64tot
- _MAX_ITOSTR_BASE16_COUNT
- _MAX_ITOSTR_BASE10_COUNT
- _MAX_ITOSTR_BASE8_COUNT
- _MAX_ITOSTR_BASE2_COUNT
- _MAX_LTOSTR_BASE16_COUNT
- _MAX_LTOSTR_BASE10_COUNT
- _MAX_LTOSTR_BASE8_COUNT
- _MAX_LTOSTR_BASE2_COUNT
- _MAX_ULTOSTR_BASE16_COUNT
- _MAX_ULTOSTR_BASE10_COUNT
- _MAX_ULTOSTR_BASE8_COUNT
- _MAX_ULTOSTR_BASE2_COUNT
- _MAX_I64TOSTR_BASE16_COUNT
- _MAX_I64TOSTR_BASE10_COUNT
- _MAX_I64TOSTR_BASE8_COUNT
- _MAX_I64TOSTR_BASE2_COUNT
- _MAX_U64TOSTR_BASE16_COUNT
- _MAX_U64TOSTR_BASE10_COUNT
- _MAX_U64TOSTR_BASE8_COUNT
- _MAX_U64TOSTR_BASE2_COUNT
helpviewer_keywords:
- _itot function
- ui64toa function
- _ui64toa function
- converting integers
- itot function
- _i64tow function
- _i64toa function
- _itow function
- ui64tow function
- integers, converting
- itoa function
- _ui64tow function
- i64tow function
- itow function
- i64toa function
- converting numbers, to strings
- _itoa function
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
ms.openlocfilehash: 016f3474345b623415be9fe33556bb9f466542ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157367"
---
# <a name="itoa-itoa-ltoa-ltoa-ultoa-ultoa-i64toa-ui64toa-itow-ltow-ultow-i64tow-ui64tow"></a>itoa – _itoa –, ltoa –, _ltoa –, ultoa –, _ultoa –, _i64toa –, _ui64toa –, _itow –, _ltow –, _ultow –, _i64tow –, _ui64tow –

Převede celé číslo na řetězec. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [_itoa_s – _itow_s – funkce](itoa-s-itow-s.md).

## <a name="syntax"></a>Syntaxe

```C
char * _itoa( int value, char *buffer, int radix );
char * _ltoa( long value, char *buffer, int radix );
char * _ultoa( unsigned long value, char *buffer, int radix );
char * _i64toa( long long value, char *buffer, int radix );
char * _ui64toa( unsigned long long value, char *buffer, int radix );

wchar_t * _itow( int value, wchar_t *buffer, int radix );
wchar_t * _ltow( long value, wchar_t *buffer, int radix );
wchar_t * _ultow( unsigned long value, wchar_t *buffer, int radix );
wchar_t * _i64tow( long long value, wchar_t *buffer, int radix );
wchar_t * _ui64tow( unsigned long long value, wchar_t *buffer, int radix );

// These Posix versions of the functions have deprecated names:
char * itoa( int value, char *buffer, int radix );
char * ltoa( long value, char *buffer, int radix );
char * ultoa( unsigned long value, char *buffer, int radix );

// The following template functions are C++ only:
template <size_t size>
char *_itoa( int value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( long value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
char *_i64toa( long long value, char (&buffer)[size], int radix );

template <size_t size>
char * _ui64toa( unsigned long long value, char (&buffer)[size], int radix );

template <size_t size>
wchar_t * _itow( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ltow( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ultow( unsigned long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _i64tow( long long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ui64tow( unsigned long long value, wchar_t (&buffer)[size],
   int radix );
```

### <a name="parameters"></a>Parametry

*value*<br/>
Číslo, které má být převeden.

*Vyrovnávací paměti*<br/>
Vyrovnávací paměti, který obsahuje výsledek převodu.

*radix*<br/>
Základ pro převod *hodnota*, která musí být v rozsahu 2 až 36.

*Velikost*<br/>
Délka vyrovnávací paměti v jednotkách, které tyto typy znaků. Tento parametr je odvozen z *vyrovnávací paměti* argument v jazyce C++.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na *vyrovnávací paměti*. Není vrácena žádná chyba.

## <a name="remarks"></a>Poznámky

**_Itoa –**, **_ltoa –**, **_ultoa –**, **_i64toa –**, a **_ui64toa –** převádějí na číslice dané *hodnotu* argument řetězec znaků zakončené znakem null a úložiště výsledků (až 33 znaků pro **_itoa –**, **_ltoa –**, a  **_ultoa –** a 65 pro **_i64toa –** a **_ui64toa –**) v *vyrovnávací paměti*. Pokud *základ číselné soustavy* rovná 10 a *hodnotu* je záporný, je první znak řetězce uložené znaménko mínus (**-**). **_Itow –**, **_ltow –**, **_ultow –**, **_i64tow –**, a **_ui64tow –** funkce jsou širokého znaku verze **_itoa –**, **_ltoa –**, **_ultoa –**, **_i64toa –**, a **_ui64toa –**, v uvedeném pořadí.

> [!IMPORTANT]
> Tyto funkce můžete napsat za koncem vyrovnávací paměť je příliš malá. Pokud chcete zabránit přetečení vyrovnávací paměti, ujistěte se, že *vyrovnávací paměti* je příliš velká pro uložení převedený číslic plus koncový znak null a znak znaménka. Nesprávné použití těchto funkcí může způsobit vážné bezpečnostní problémy ve vašem kódu.

Z důvodu jejich potenciál pro problémy se zabezpečením, ve výchozím nastavení, tyto funkce způsobí upozornění na vyřazení [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **Tato funkce nebo proměnná může nebezpečné. Zvažte použití** *safe_function* **místo. Pokud chcete zakázat vyřazení, použijte _CRT_SECURE_NO_WARNINGS.** Doporučujeme změnit zdrojový kód Refaktorovat pro použití *safe_function* navrhl upozornění. Bezpečnějšími funkcemi Nezapisovat více znaků, než zadaná velikost vyrovnávací paměti. Další informace najdete v tématu [_itoa_s – _itow_s – funkce](itoa-s-itow-s.md).

Použití těchto funkcí bez upozornění na vyřazení, definujte **_CRT_SECURE_NO_WARNINGS** preprocesor makro před zahrnutím záhlaví CRT. Můžete to provést na příkazovém řádku v příkazovém řádku pro vývojáře tak, že přidáte **/D_CRT_SECURE_NO_WARNINGS** – možnost kompilátoru do **cl** příkazu. Jinak definujte makro ve zdrojových souborech. Pokud používáte předkompilovaných hlaviček, definujte makro v horní části předkompilované hlavičky zahrnout soubor stdafx.h obvykle. Chcete-li definovat makro ve zdrojovém kódu, použijte **#define** směrnice před obsahovat libovolné záhlaví CRT, jako v následujícím příkladu:

```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

V jazyce C++ mají tyto funkce přetížení šablon, které vyvolávají jejich protějšky bezpečnější. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

POSIX – názvy **itoa –**, **ltoa –**, a **ultoa –** existovat jako aliasy pro **_itoa –**, **_ltoa –**, a **_ultoa –** funkce. POSIX – názvy jsou zastaralé, protože nepostupujte podle konvence název specifický pro implementaci funkce ISO c. Ve výchozím nastavení, tyto funkce způsobí upozornění na vyřazení [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **POSIX název pro tuto položku je zastaralý. Místo toho použijte ISO C a C++ splňovala podmínky shody názvu:** *nový_název*. Doporučujeme změnit zdrojový kód používat bezpečnější verze těchto funkcí, **_itoa_s –**, **_ltoa_s –**, nebo **_ultoa_s –**. Další informace najdete v tématu [_itoa_s – _itow_s – funkce](itoa-s-itow-s.md).

Pro přenositelnost zdrojového kódu můžete chtít zachovat POSIX – názvy v kódu. Použití těchto funkcí bez upozornění na vyřazení, definovat, jak **_CRT_NONSTDC_NO_WARNINGS** a **_CRT_SECURE_NO_WARNINGS** makra preprocesoru před zahrnutím záhlaví CRT. Můžete to provést na příkazovém řádku v příkazovém řádku pro vývojáře tak, že přidáte **/D_CRT_SECURE_NO_WARNINGS** a **/D_CRT_NONSTDC_NO_WARNINGS** možností kompilátoru k **cl**příkazu. Jinak definujte makra ve zdrojových souborech. Pokud používáte předkompilovaných hlaviček, definování makra v horní části předkompilované hlavičky zahrnout soubor stdafx.h obvykle. Chcete-li definovat makra ve zdrojovém kódu, použijte **#define** direktivy před obsahovat libovolné záhlaví CRT, jako v následujícím příkladu:

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>Makra převodu maximální počet

Knihovna CRT vám pomůže vytvořit zabezpečené vyrovnávací paměti pro převody, zahrnuje některé vhodné makra. Tyto definují velikost vyrovnávací paměti vyžadované k převodu nejdelší možnou hodnotu každého celočíselného typu, včetně ukončovacího znaku null a podepsat znak, pro několik běžných základních tříd. K zajištění, že vaši převod vyrovnávací paměť je příliš velká pro získání jakýkoli převod v základu podle *základ číselné soustavy*, použijte některou z těchto definice makra při přidělení vyrovnávací paměti. To pomáhá zabránit chybám přetečení vyrovnávací paměti při převodu celočíselné typy řetězců. Tato makra jsou definovány, jakmile zahrnete stdlib.h nebo wchar.h ve zdroji.

Pokud chcete použít jeden z těchto maker v funkce pro převod řetězce, vaše převod vyrovnávací paměti odpovídající znak typu deklarace a používání hodnotu makra pro typ integer a základní jako dimenze vyrovnávací paměti. Tato tabulka obsahuje makra, které jsou vhodné pro každou funkci pro uvedených základních tříd:

||||
|-|-|-|
|Funkce|radix|Makra|
|**_itoa**, **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**, **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**, **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**, **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**, **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

Tento příklad používá k definování dostatečně velký, aby obsahovala vyrovnávací paměť počet makra převodu **unsigned long long.** v základní 2:

```cpp
#include <wchar.h>
#include <iostream>
int main()
{
    wchar_t buffer[_MAX_U64TOSTR_BASE2_COUNT];
    std:wcout << _ui64tow(0xFFFFFFFFFFFFFFFFull, buffer, 2) << std::endl;
}
```

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot**|**_itoa**|**_itoa**|**_itow**|
|**_ltot**|**_ltoa**|**_ltoa**|**_ltow**|
|**_ultot –**|**_ultoa**|**_ultoa**|**_ultow**|
|**_i64tot**|**_i64toa**|**_i64toa**|**_i64tow**|
|**_ui64tot**|**_ui64toa**|**_ui64toa**|**_ui64tow**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**itoa**, **ltoa**, **ultoa**|\<stdlib.h>|
|**_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, **_ui64toa**|\<stdlib.h>|
|**_itow**, **_ltow**, **_ultow**, **_i64tow**, **_ui64tow**|\<stdlib.h > nebo \<wchar.h >|

Tyto funkce a makra jsou specifické pro společnost Microsoft. Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento příklad znázorňuje použití některých funkcí převodu celého čísla. Všimněte si, **_CRT_SECURE_NO_WARNINGS** – makro do nečinnosti upozornění C4996.

```C
// crt_itoa.c
// Compile by using: cl /W4 crt_itoa.c
// This program makes use of the _itoa functions
// in various examples.

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen
#include <stdlib.h>     // for _countof, _itoa fns, _MAX_COUNT macros

int main(void)
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;

    for (r = 10; r >= 2; --r)
    {
        _itoa(-1, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _i64toa(-1LL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _ui64toa(0xffffffffffffffffULL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
}
```

```Output
base 10: -1 (2 chars)
base 9: 12068657453 (11 chars)
base 8: 37777777777 (11 chars)
base 7: 211301422353 (12 chars)
base 6: 1550104015503 (13 chars)
base 5: 32244002423140 (14 chars)
base 4: 3333333333333333 (16 chars)
base 3: 102002022201221111210 (21 chars)
base 2: 11111111111111111111111111111111 (32 chars)

base 10: -1 (2 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)

base 10: 18446744073709551615 (20 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[_itoa_s – _itow_s – funkce](itoa-s-itow-s.md)<br/>
