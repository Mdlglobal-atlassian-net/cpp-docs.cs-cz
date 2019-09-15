---
title: _itoa, funkce _itow
ms.date: 08/19/2019
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
ms.openlocfilehash: 97085ab8a8c720d278374868f9b1c90a91a6da3b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953573"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa, _itoa, ltoa, _ltoa, ultoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, _ultow, _i64tow, _ui64tow

Převede celé číslo na řetězec. K dispozici jsou bezpečnější verze těchto funkcí; viz [_itoa_s, _itow_s Functions](itoa-s-itow-s.md).

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
Číslo, které má být převedeno.

*vyrovnávací paměti*<br/>
Vyrovnávací paměť, která obsahuje výsledek převodu.

*radix*<br/>
Základ pro převod *hodnoty*, která musí být v rozsahu 2-36.

*hodnota*<br/>
Délka vyrovnávací paměti v jednotkách typu znaku. Tento parametr je odvozený od argumentu *buffer* v C++.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na *vyrovnávací paměť*. Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Funkce **_itoa**, **_ltoa**, **_ultoa**, **_i64toa**a **_ui64toa** převádějí číslice daného argumentu *hodnoty* na řetězec znaků zakončený hodnotou null a uloží výsledek (až 33 znaků pro **_itoa.** , **_ltoa**a **_ultoa**a 65 pro **_i64toa** a **_ui64toa**) ve *vyrovnávací paměti*. Pokud se *základ* rovná 10 a *hodnota* je záporná, je prvním znakem uloženého řetězce znaménko mínus ( **-** ). Funkce **_itow**, **_ltow**, **_ultow**, **_i64tow**a **_ui64tow** jsou verze s libovolným znakem **_itoa**, **_ltoa**, **_ultoa**, **_i64toa**a **_ui64toa**, v uvedeném pořadí.

> [!IMPORTANT]
> Tyto funkce mohou zapisovat za konec vyrovnávací paměti, která je příliš malá. Chcete-li zabránit přetečení vyrovnávací paměti, zajistěte, aby byla *vyrovnávací paměť* dostatečně velká, aby obsahovala převedené číslice, a znak null a znak znaménka. Zneužití těchto funkcí může způsobit vážné problémy se zabezpečením v kódu.

Z důvodu potenciálních problémů se zabezpečením tyto funkce ve výchozím nastavení způsobují [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)upozornění na vyřazení: **Tato funkce nebo proměnná může být nebezpečná. Místo toho** zvažte použití *safe_function* **. Pokud chcete zakázat zastaralost, použijte _CRT_SECURE_NO_WARNINGS.** Doporučujeme, abyste změnili zdrojový kód tak, aby používal *safe_function* navržený zprávou upozornění. Bezpečnější funkce nezapisují více znaků, než je zadaná velikost vyrovnávací paměti. Další informace najdete v tématu [_itoa_s, _itow_s Functions](itoa-s-itow-s.md).

Chcete-li použít tyto funkce bez upozornění na vyřazení, definujte před zahrnutím hlaviček CRT **_CRT_SECURE_NO_WARNINGS** makro preprocesoru. To můžete provést na příkazovém řádku v příkazovém řádku vývojáře přidáním možnosti kompilátoru **/D_CRT_SECURE_NO_WARNINGS** do příkazu **CL** . V opačném případě definujte makro ve zdrojových souborech. Použijete-li předkompilované hlavičky, definujte makro v horní části předkompilované hlavičky Include File, *PCH. h* (*stdafx. h* v aplikaci Visual Studio 2017 a starší). Chcete-li definovat makro ve zdrojovém kódu, použijte direktivu **#define** před zahrnutím jakékoli hlavičky CRT, jako v tomto příkladu:

```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

V C++nástroji mají tyto funkce přetížení šablony, která vyvolává jejich bezpečnější protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Názvy POSIX **itoa**, **ltoa**a **ultoa** existují jako aliasy pro funkce **_itoa**, **_ltoa**a **_ultoa** . Názvy POSIX jsou zastaralé, protože nenásledují konvence názvů funkcí specifických pro implementaci ISO C. Ve výchozím nastavení tyto funkce způsobují [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)upozornění na zastaralé: **Název POSIX pro tuto položku je zastaralý. Místo toho použijte ISO C a C++ vyhovující název:** *new_name*. Doporučujeme, abyste změnili zdrojový kód tak, aby používal bezpečnější verze těchto funkcí, **_itoa_s**, **_ltoa_s**nebo **_ultoa_s**. Další informace najdete v tématu [_itoa_s, _itow_s Functions](itoa-s-itow-s.md).

Pro přenositelnost zdrojového kódu můžete chtít zachovat názvy POSIX ve vašem kódu. Chcete-li použít tyto funkce bez upozornění na vyřazení, před zahrnutím všech hlaviček CRT definujte jak makra preprocesoru **_CRT_NONSTDC_NO_WARNINGS** , tak **_CRT_SECURE_NO_WARNINGS** . To můžete provést na příkazovém řádku v příkazovém řádku vývojáře přidáním možností kompilátoru **/D_CRT_SECURE_NO_WARNINGS** a **/D_CRT_NONSTDC_NO_WARNINGS** do příkazu **CL** . V opačném případě definujte makra ve zdrojových souborech. Pokud používáte předkompilované hlavičky, definujte makra v horní části souboru include předkompilované hlavičky. Chcete-li definovat makra ve zdrojovém kódu, použijte direktivy **#define** před zahrnutím jakékoli hlavičky CRT, jako v tomto příkladu:

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>Makra maximálního počtu převodů

Pro usnadnění vytváření zabezpečených vyrovnávacích pamětí pro převody zahrnuje CRT i některá užitečná makra. Ty definují velikost vyrovnávací paměti potřebné k převodu nejdelší možné hodnoty každého typu celého čísla, včetně ukončovacího znaku null a znaku znaménka pro několik běžných základů. Aby bylo zajištěno, že vyrovnávací paměť pro převod je dostatečně velká pro příjem převodu v základní třídě určené podle *základu*, použijte při přidělování vyrovnávací paměti jedno z těchto definovaných maker. To pomáhá zabránit chybám přetečení vyrovnávací paměti při převodu integrálních typů na řetězce. Tato makra jsou definována, když ve zdroji zadáte buď Stdlib. h, nebo WCHAR. h.

Chcete-li použít jedno z těchto maker ve funkci pro převod řetězce, deklarujte vyrovnávací paměť pro převod příslušného typu znaku a použijte hodnotu makra pro celočíselný typ a základ jako dimenzi vyrovnávací paměti. Tato tabulka uvádí makra, která jsou vhodná pro jednotlivé funkce v uvedených základech:

||||
|-|-|-|
|Funkce|radix|Makra|
|**_itoa**, **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**, **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**, **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**, **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**, **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

V tomto příkladu se používá makro Count (počet převodů) k definování vyrovnávací paměti, která je dostatečně velká, aby v základní třídě 2 obsahovala **nepodepsané dlouhé** znaky

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
|**_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, **_ui64toa**|\<stdlib.h>|
|**_itow**, **_ltow**, **_ultow**, **_i64tow**, **_ui64tow**|\<Stdlib. h > nebo \<WCHAR. h >|

Tyto funkce a makra jsou specifické pro společnost Microsoft. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tato ukázka demonstruje použití některých funkcí konverze celého čísla. Všimněte si použití makra **_CRT_SECURE_NO_WARNINGS** k tiché výstraze C4996.

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
[_itoa_s, funkce _itow_s](itoa-s-itow-s.md)<br/>
