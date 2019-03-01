---
title: vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l
ms.date: 11/04/2016
apiname:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
helpviewer_keywords:
- vsnwprintf_s function
- _vsntprintf_s function
- _vsntprintf_s_l function
- vsntprintf_s function
- vsnwprintf_s_l function
- vsnprintf_s_l function
- vsntprintf_s_l function
- _vsnwprintf_s_l function
- _vsnprintf_s function
- vsnprintf_s function
- _vsnprintf_s_l function
- _vsnwprintf_s function
- formatted text [C++]
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
ms.openlocfilehash: 255c3b760dec1495a4f9a82915878a5504844f24
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210702"
---
# <a name="vsnprintfs-vsnprintfs-vsnprintfsl-vsnwprintfs-vsnwprintfsl"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l

Zapíše formátovaný výstup pomocí ukazatele na seznam argumentů. Jde o verzích [vsnprintf – _vsnprintf –, _vsnprintf_l –, _vsnwprintf –, _vsnwprintf_l –](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int _vsnprintf_s(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_s(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro výstup.

*sizeOfBuffer*<br/>
Velikost *vyrovnávací paměti* výstupu jako počet znaků.

*Počet*<br/>
Maximální počet znaků pro zápis (nezahrnuje ukončující znak null), nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*Formát*<br/>
Specifikace formátu.

*argptr*<br/>
Ukazatel na seznam argumentů.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

**vsnprintf_s –**, **_vsnprintf_s –** a **_vsnwprintf_s –** vrátí počet napsaných znaků, nikoli včetně ukončujícího znaku null, nebo zápornou hodnotu, pokud dojde k chybě výstupu. **vsnprintf_s –** je stejný jako **_vsnprintf_s –**. **vsnprintf_s –** je součástí shody se standardem ANSI. **_vnsprintf** se zachovává kvůli zpětné kompatibilitě.

Pokud úložiště potřebné pro ukládání dat a ukončujícího znaku null překročí *sizeOfBuffer*, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md), není-li *počet*  je [_TRUNCATE](../../c-runtime-library/truncate.md), v takovém případě největší část řetězce jako se vejde *vyrovnávací paměti* je zapsána a je vrácena hodnota -1. Pokud po obslužnou rutinu neplatného parametru pokračuje v provádění, tyto funkce nastaví *vyrovnávací paměti* na prázdný řetězec, nastavit **errno** k **ERANGE**a vrátí hodnotu -1.

Pokud *vyrovnávací paměti* nebo *formátu* je **NULL** ukazatele, nebo pokud *počet* je menší než nebo rovna nule, je vyvolána obslužná rutina neplatného parametru. Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1.

### <a name="error-conditions"></a>Chybové podmínky

|**Podmínka**|Vrátí|**errno**|
|-----------------|------------|-------------|
|*vyrovnávací paměť* je **NULL**|-1|**EINVAL**|
|*Formát* je **NULL**|-1|**EINVAL**|
|*počet* < = 0|-1|**EINVAL**|
|*sizeOfBuffer* příliš malý (a *počet* ! = **_TRUNCATE**)|-1 (a *vyrovnávací paměti* nastavenou na prázdný řetězec)|**ERANGE**|

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí bere ukazatel na seznam argumentů a potom formátuje a zapíše *počet* znaků určených parametrem do paměti na které odkazuje *vyrovnávací paměti* a připojí ukončující znak null.

Pokud *počet* je [_TRUNCATE](../../c-runtime-library/truncate.md), tyto funkce zapíší co největší část řetězce, jak se vejde *vyrovnávací paměti* a ponechají prostor pro ukončující znak null. Pokud se vejde celý řetězec (s ukončujícím znakem null) *vyrovnávací paměti*, pak tyto funkce vrátí počet znaků zapsaných (nezahrnuje ukončující znak null); v opačném případě tyto funkce vrátí -1 pro označení této zkrácení došlo k chybě.

Verze těchto funkcí s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí předaného namísto aktuálního národní prostředí pro vlákno.

> [!IMPORTANT]
> Ujistěte se, že *formátu* není uživatelem definovaný řetězec. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

> [!NOTE]
> Aby se zajistilo, že existuje místo pro ukončující znak null, ujistěte se, že *počet* je striktně menší než délka vyrovnávací paměti, nebo použijte **_TRUNCATE**.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (tím eliminuje nutnost zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h > a \<stdarg.h >|\<varargs.h>*|
|**_vsnprintf_s**, **_vsnprintf_s_l**|\<stdio.h > a \<stdarg.h >|\<varargs.h>*|
|**_vsnwprintf_s**, **_vsnwprintf_s_l**|\<stdio.h > nebo \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|

\* Vyžaduje se pro kompatibility systému UNIX V.

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```cpp
// crt_vsnprintf_s.cpp
#include <stdio.h>
#include <wtypes.h>

void FormatOutput(LPCSTR formatstring, ...)
{
   int nSize = 0;
   char buff[10];
   memset(buff, 0, sizeof(buff));
   va_list args;
   va_start(args, formatstring);
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);
   printf("nSize: %d, buff: %s\n", nSize, buff);
   va_end(args);
}

int main() {
   FormatOutput("%s %s", "Hi", "there");
   FormatOutput("%s %s", "Hi", "there!");
   FormatOutput("%s %s", "Hi", "there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
