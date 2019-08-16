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
ms.openlocfilehash: 50e38e3177462f17436727cf26d1e7dade9cb882
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499088"
---
# <a name="vsnprintf_s-_vsnprintf_s-_vsnprintf_s_l-_vsnwprintf_s-_vsnwprintf_s_l"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l

Zapíše formátovaný výstup pomocí ukazatele na seznam argumentů. Jedná se o verze [vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) s vylepšeními zabezpečení, jak [je popsáno v části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*vyrovnávací paměti*<br/>
Umístění úložiště pro výstup.

*sizeOfBuffer*<br/>
Velikost *vyrovnávací paměti* pro výstup, jako počet znaků.

*výpočtu*<br/>
Maximální počet znaků, které mají být zapsány (nezahrnují ukončující hodnotu null) nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*format*<br/>
Specifikace formátu.

*argptr*<br/>
Ukazatel na seznam argumentů.

*jazyka*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

**vsnprintf_s**, **_vsnprintf_s** a **_vsnwprintf_s** vrátí počet zapsaných znaků, včetně ukončující hodnoty null, nebo zápornou hodnotu, pokud dojde k chybě výstupu. **vsnprintf_s** je shodná s **_vsnprintf_s**. **vsnprintf_s** je součástí dodržování předpisů standardu ANSI. **_vnsprintf** se zachovává kvůli zpětné kompatibilitě.

Pokud úložiště potřebné pro uložení dat a ukončující hodnotu null překračuje *sizeOfBuffer*, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md), pokud *Count* není [_TRUNCATE](../../c-runtime-library/truncate.md), v takovém případě jako velká část řetězec, který se vejde do *vyrovnávací paměti* , se zapíše a vrátí-1. Pokud provádění pokračuje po obslužné rutině neplatného parametru, nastaví tyto funkce *vyrovnávací paměť* na prázdný řetězec, nastaví **errno** na **ERANGE**a vrátí-1.

Pokud je *vyrovnávací paměť* nebo *Formát* ukazatel s **hodnotou null** , nebo pokud je *počet* menší nebo roven nule, je vyvolána obslužná rutina neplatného parametru. Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí-1.

### <a name="error-conditions"></a>Chybové stavy

|**Pomocné**|Vrátit|**errno**|
|-----------------|------------|-------------|
|*vyrovnávací paměť* má **hodnotu null** .|-1|**EINVAL**|
|*Formát* je **null** .|-1|**EINVAL**|
|*počet* < = 0|-1|**EINVAL**|
|*sizeOfBuffer* je příliš malý (a *Count* ! = **_TRUNCATE**).|-1 (a *vyrovnávací paměť* je nastavená na prázdný řetězec)|**ERANGE**|

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí bere ukazatel na seznam argumentů a potom formátuje a zapisuje do *počtu* znaků daných dat do paměti, na kterou ukazuje *vyrovnávací paměť* , a připojuje ukončující hodnotu null.

Pokud je počet [_TRUNCATE](../../c-runtime-library/truncate.md), pak tyto funkce zapisují tolik řetězce, jako by se vešly do *vyrovnávací paměti* , a ponechají prostor pro ukončující hodnotu null. Pokud se celý řetězec (s ukončujícím znakem null) vejde do *vyrovnávací paměti*, pak tyto funkce vrátí počet zapsaných znaků (bez ukončující hodnoty null); v opačném případě tyto funkce vrátí hodnotu-1, která označuje, že došlo ke zkrácení.

Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí vlákna.

> [!IMPORTANT]
> Ujistěte se, že *Formát* není uživatelem definovaný řetězec. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

> [!NOTE]
> Aby bylo zajištěno, že pro ukončující hodnotu null existuje prostor, ujistěte se, že je *počet* striktně menší než délka vyrovnávací paměti, nebo použijte **_TRUNCATE**.

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio. h > a \<STDARG. h >|\<varargs.h>*|
|**_vsnprintf_s**, **_vsnprintf_s_l**|\<stdio. h > a \<STDARG. h >|\<varargs.h>*|
|**_vsnwprintf_s**, **_vsnwprintf_s_l**|\<stdio. h > nebo \<WCHAR. h > a \<STDARG. h >|\<varargs.h>*|

\*Vyžaduje se pro kompatibilitu se systémem UNIX V.

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
