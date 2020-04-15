---
title: _itoa, _itow funkce
ms.date: 4/2/2020
api_name:
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
- _o__i64toa
- _o__i64tow
- _o__itoa
- _o__itow
- _o__ltoa
- _o__ltow
- _o__ui64toa
- _o__ui64tow
- _o__ultoa
- _o__ultow
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 0cc084076c5e39843ecc1afa08671ce6b2f06d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342704"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa, _itoa, ltoa, _ltoa, ultoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, _ultow, _i64tow, _ui64tow

Převede celé číslo na řetězec. K dispozici jsou bezpečnější verze těchto funkcí. viz [_itoa_s, _itow_s funkce](itoa-s-itow-s.md).

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

// These POSIX versions of the functions have deprecated names:
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

*Hodnotu*<br/>
Číslo, které má být převedeno.

*Vyrovnávací paměti*<br/>
Vyrovnávací paměť, která obsahuje výsledek převodu.

*Radix*<br/>
Základ pro převod *hodnoty*, který musí být v rozsahu 2-36.

*Velikost*<br/>
Délka vyrovnávací paměti v jednotkách typu znaku. Tento parametr je odvozen z argumentu *vyrovnávací paměti* v jazyce C++.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí ukazatel vyrovnávací *paměti*. Neexistuje žádná chyba vrátit.

## <a name="remarks"></a>Poznámky

Funkce **_itoa**, **_ltoa**, **_ultoa**, **_i64toa**a **_ui64toa** převedou číslice argumentu dané *hodnoty* na řetězec znaků ukončený hodnotou null a výsledek uloží (až 33 znaků pro **_itoa**, **_ltoa**a **_ultoa**a 65 pro **_i64toa** a **_ui64toa**) do *vyrovnávací paměti*. Pokud *radix* rovná 10 a *hodnota* je záporná, první znak**-** uloženého řetězce je znaménko mínus ( ). **Funkce _itow**, **_ltow**, **_ultow**, **_i64tow**a **_ui64tow** jsou širokoznakové verze **_itoa**, **_ltoa**, **_ultoa**, **_i64toa**a **_ui64toa**.

> [!IMPORTANT]
> Tyto funkce můžete zapsat za konec vyrovnávací paměti, která je příliš malá. Chcete-li zabránit přetečení vyrovnávací paměti, ujistěte se, že *vyrovnávací paměť* je dostatečně velký pro uložení převedené číslice plus koncové null-znak a znak znak. Zneužití těchto funkcí může způsobit vážné problémy se zabezpečením ve vašem kódu.

Z důvodu jejich potenciálu pro problémy se zabezpečením, ve výchozím nastavení tyto funkce způsobit upozornění vyřazení [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **Tato funkce nebo proměnná může být nebezpečné. Zvažte použití** *safe_function* **místo. Chcete-li zakázat vyřazení, použijte _CRT_SECURE_NO_WARNINGS.** Doporučujeme změnit zdrojový kód tak, aby používal *safe_function* navržený varovnou zprávou. Bezpečnější funkce nezapisují více znaků, než je zadaná velikost vyrovnávací paměti. Další informace naleznete [v tématu _itoa_s, _itow_s funkce](itoa-s-itow-s.md).

Chcete-li tyto funkce použít bez upozornění na vyřazení, definujte **_CRT_SECURE_NO_WARNINGS** makro preprocesoru před zahrnutím všech hlaviček CRT. Můžete to provést na příkazovém řádku v příkazovém řádku vývojáře přidáním možnosti kompilátoru **/D_CRT_SECURE_NO_WARNINGS** do příkazu **cl.** V opačném případě definujte makro ve zdrojových souborech. Pokud používáte předkompilovaná záhlaví, definujte makro v horní části předkompilované hlavičky zahrnout soubor *pch.h* (*stdafx.h* v sadě Visual Studio 2017 a starší). Chcete-li definovat makro ve zdrojovém kódu, použijte **#define** direktivu před zahrnutím libovolné hlavičky CRT, jako v tomto příkladu:

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

V jazyce C++ mají tyto funkce přetížení šablony, které vyvolávají jejich bezpečnější protějšky. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Názvy POSIX **itoa**, **ltoa**a **ultoa** existují jako aliasy pro funkce **_itoa**, **_ltoa**a **_ultoa.** Názvy POSIX jsou zastaralé, protože nedodržují konvence globálních názvů funkcí specifických pro implementaci iso C. Ve výchozím nastavení tyto funkce způsobit upozornění vyřazení [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **Název POSIX pro tuto položku je zastaralé. Místo toho použijte název conformant ISO C a C++:** *new_name*. Doporučujeme změnit zdrojový kód tak, aby používal bezpečnější verze těchto funkcí, **_itoa_s**, **_ltoa_s**nebo **_ultoa_s**. Další informace naleznete [v tématu _itoa_s, _itow_s funkce](itoa-s-itow-s.md).

Pro přenositelnost zdrojového kódu můžete upřednostnit názvy POSIX v kódu. Chcete-li tyto funkce použít bez upozornění na vyřazení, definujte **_CRT_NONSTDC_NO_WARNINGS** a **_CRT_SECURE_NO_WARNINGS** preprocesorová makra před zahrnutím všech hlaviček CRT. Můžete to provést na příkazovém řádku v příkazovém řádku vývojáře přidáním **/D_CRT_SECURE_NO_WARNINGS** a **/D_CRT_NONSTDC_NO_WARNINGS** možnosti kompilátoru do příkazu **cl.** V opačném případě definujte makra ve zdrojových souborech. Pokud používáte předkompilovaná záhlaví, definujte makra v horní části souboru zahrnutí předkompilované hlavičky. Chcete-li definovat makra ve zdrojovém kódu, použijte **#define** direktivy před zahrnutím libovolné hlavičky CRT, jako v tomto příkladu:

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>Maximální počet převodů makra

CrT obsahuje některá praktická makra, které vám pomohou vytvořit zabezpečené vyrovnávací paměti pro převody. Ty definují velikost vyrovnávací paměti potřebné k převodu nejdelší možnou hodnotu každého typu celé číslo, včetně null zakončení a znak znaku, pro několik společných základů. Chcete-li zajistit, aby vyrovnávací paměť pro převod byla dostatečně velká, aby bylo dosaženo převodu v základně určené *parametrem radix*, použijte při přidělovat vyrovnávací paměť jedno z těchto definovaných maker. To pomáhá zabránit chybám přetečení vyrovnávací paměti při převodu integrální typy na řetězce. Tato makra jsou definována, pokud do zdroje zahrnete soubor stdlib.h nebo wchar.h.

Chcete-li použít jedno z těchto maker ve funkci převodu řetězce, deklarujte vyrovnávací paměť převodu příslušného typu znaku a použijte hodnotu makra pro typ celé číslo a základnu jako dimenzi vyrovnávací paměti. V této tabulce jsou uvedena makra, která jsou vhodná pro každou funkci pro uvedené základy:

||||
|-|-|-|
|Functions|Radix|Makra|
|**_itoa**, **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa** **, _ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**, **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa** **, _i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**, **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

Tento příklad používá makro počtu převodů k definování vyrovnávací paměti dostatečně velké, aby **obsahovala neznaménku dlouhou dlouhou** v základu 2:

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
|**_ultot**|**_ultoa**|**_ultoa**|**_ultow**|
|**_i64tot**|**_i64toa**|**_i64toa**|**_i64tow**|
|**_ui64tot**|**_ui64toa**|**_ui64toa**|**_ui64tow**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**itoa**, **ltoa**, **ultoa**|\<stdlib.h>|
|**_itoa**, **_ltoa**, **_ui64toa** **_ultoa**, **_i64toa _ui64toa**|\<stdlib.h>|
|**_itow**, **_ltow**, **_ui64tow** **_ultow _i64tow** **_ui64tow**|\<stdlib.h> \<nebo wchar.h>|

Tyto funkce a makra jsou specifické pro společnost Microsoft. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tato ukázka ukazuje použití některých funkcí převodu celé číslo. Všimněte si použití **_CRT_SECURE_NO_WARNINGS** makro k umlčení upozornění C4996.

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

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[_itoa_s, _itow_s funkce](itoa-s-itow-s.md)<br/>
