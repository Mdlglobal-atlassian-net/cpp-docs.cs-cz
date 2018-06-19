---
title: vsnprintf_s –, _vsnprintf_s –, _vsnprintf_s_l –, _vsnwprintf_s –, _vsnwprintf_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66fd7c468e516c25e2c2b408b8c1112061eeb5e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417939"
---
# <a name="vsnprintfs-vsnprintfs-vsnprintfsl-vsnwprintfs-vsnwprintfsl"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l

Zapíše formátovaný výstup pomocí ukazatele na seznam argumentů. Toto jsou verze [vsnprintf –, _vsnprintf –, _vsnprintf_l –, _vsnwprintf –, _vsnwprintf_l –](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Maximální počet znaků k zápisu (nikoli včetně ukončující null), nebo [_truncate –](../../c-runtime-library/truncate.md).

*Formát*<br/>
Specifikace formátu.

*argptr*<br/>
Ukazatel na seznam argumentů.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

**vsnprintf_s –**, **_vsnprintf_s –** a **_vsnwprintf_s –** vrátí počet znaků zapsána, pokud dojde k chybě výstup není včetně ukončující hodnotu null nebo záporná hodnota. **vsnprintf_s –** je stejný jako **_vsnprintf_s –**. **vsnprintf_s –** je zahrnuté pro dodržování předpisů pro standardu ANSI. **_vnsprintf** se zachovává kvůli zpětné kompatibilitě.

Pokud překročí úložiště potřebné pro uložení dat a ukončující null *sizeOfBuffer*, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md), pokud *počet*  je [_truncate –](../../c-runtime-library/truncate.md), v takovém případě co nejvíc řetězec tak, jak se vejde *vyrovnávací paměti* je zapsán a vrátí hodnotu -1. Pokud pokračuje v provádění po obslužná rutina neplatný parametr, nastavte tyto funkce *vyrovnávací paměti* na prázdný řetězec, nastavte **errno** k **erange –** a vrátí hodnotu -1.

Pokud *vyrovnávací paměti* nebo *formátu* je **NULL** ukazatele, nebo pokud *počet* je menší než nebo rovna nule, je volána obslužná rutina neplatný parametr. Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátí hodnotu -1.

### <a name="error-conditions"></a>Chybové stavy

|**Podmínka**|Vrátí|**Kód chyby**|
|-----------------|------------|-------------|
|*vyrovnávací paměť* je **hodnotu NULL.**|-1|**EINVAL –**|
|*Formát* je **hodnotu NULL.**|-1|**EINVAL –**|
|*počet* < = 0|-1|**EINVAL –**|
|*sizeOfBuffer* příliš malý (a *počet* ! = **_truncate –**)|-1 (a *vyrovnávací paměti* nastavit na prázdný řetězec)|**ERANGE –**|

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí má ukazatel na seznam argumentů, pak naformátuje a zapíše až *počet* znaků, který daná data na paměť na kterou odkazuje *vyrovnávací paměti* a připojí ukončující hodnotu null.

Pokud *počet* je [_truncate –](../../c-runtime-library/truncate.md), pak tyto funkce zápisu co nejvíc řetězce, který se vejde *vyrovnávací paměti* a nechat místo pro ukončující hodnotu null. Pokud celý řetězec (s ukončující null) se vejde *vyrovnávací paměti*, pak tyto funkce vrátí počet znaků, které jsou zapsány (včetně není ukončující null); jinak, tyto funkce vrátí hodnotu -1 označíte, že zkrácení došlo k chybě.

Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.

> [!IMPORTANT]
> Ujistěte se, že *formát* není řetězec definovaný uživatelem. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).

> [!NOTE]
> Aby bylo zajištěno, že prostor pro ukončující null, ujistěte *počet* je striktně menší než velikost vyrovnávací paměti, nebo použijte **_truncate –**.

V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s –**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l –**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|-------------|---------------------|----------------------|
|**vsnprintf_s –**|\<stdio.h > a \<stdarg.h >|\<varargs.h>*|
|**_vsnprintf_s –**, **_vsnprintf_s_l –**|\<stdio.h > a \<stdarg.h >|\<varargs.h>*|
|**_vsnwprintf_s –**, **_vsnwprintf_s_l –**|\<stdio.h > nebo \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|

\* Vyžaduje se pro kompatibility V systému UNIX.

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
