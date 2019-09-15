---
title: vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l
ms.date: 11/04/2016
api_name:
- _vsnprintf
- _vsnprintf_l
- _vsnwprintf
- _vsnwprintf_l
- _vsnprintf
- _vsnprintf;
- vsnprintf; _vsnprintf
- _vsnwprintf;
- _vsnprintf_l;
- _vsnwprintf_l;
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
- ntoskrnl.exe
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vsnprintf
- _vsnwprintf
- _vsntprintf
- vsnprintf
- stdio/vsnprintf
- stdio/_vsnprintf
- stdio/_vsnprintf_l
- stdio/_vsnwprintf
- stdio/_vsnwprintf_l
- _vsnprintf_l
- _vsnwprintf_l
helpviewer_keywords:
- vsntprintf function
- _vsnwprintf_l function
- vsnwprintf_l function
- vsntprintf_l function
- _vsntprintf function
- _vsnprintf_l function
- vsnprintf function
- _vsntprintf_l function
- vsnprintf_l function
- _vsnwprintf function
- _vsnprintf function
- formatted text [C++]
- vsnwprintf function
ms.assetid: a97f92df-c2f8-4ea0-9269-76920d2d566a
ms.openlocfilehash: 721ea80272f7a76e959528ec4114d69bd0e80507
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945313"
---
# <a name="vsnprintf-_vsnprintf-_vsnprintf_l-_vsnwprintf-_vsnwprintf_l"></a>vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l

Zapíše formátovaný výstup pomocí ukazatele na seznam argumentů. K dispozici jsou bezpečnější verze těchto funkcí; viz [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
int vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_l(
   char *buffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf_l(
   char (&buffer)[size],
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_l(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Umístění úložiště pro výstup.

*výpočtu*<br/>
Maximální počet znaků, které mají být zapsány.

*format*<br/>
Specifikace formátu.

*argptr*<br/>
Ukazatel na seznam argumentů.

*jazyka*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

Funkce **vsnprintf** vrací počet zapsaných znaků a nepočítá ukončující znak null. Pokud velikost vyrovnávací paměti určená parametrem *Count* není dostatečně velká, aby obsahovala výstup určený parametrem *Format* a *argptr*, návratová hodnota **vsnprintf** je počet znaků, které by byly zapsány, a nepočítá hodnotu null. znak, pokud byl *počet* dostatečně velký. Pokud je vrácená hodnota větší než *Count* -1, výstup byl zkrácen. Návratová hodnota-1 označuje, že došlo k chybě kódování.

Funkce **_vsnprintf** a **_vsnwprintf** vrací počet znaků zapsaných v případě, že počet znaků, které mají být zapsány, je menší nebo roven *počtu*; Pokud je počet znaků, které mají být zapsány, větší než *počet*, vrátí tyto funkce-1 znamenající, že výstup byl zkrácen.

Hodnota vrácená všemi těmito funkcemi nezahrnuje ukončující hodnotu null, ať už je zapsána, nebo ne. Pokud je *počet* nula, vrácená hodnota je počet znaků, které funkce zapisují, a ne včetně ukončujících hodnot null. Tento výsledek lze použít k přidělení dostatečného prostoru pro ukládání do vyrovnávací paměti pro řetězec a jeho ukončující hodnotu null a poté volání funkce pro vyplňování vyrovnávací paměti.

Pokud má formát **hodnotu null**nebo pokud je *vyrovnávací paměť* **null** a *počet* není roven nule, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí bere ukazatel na seznam argumentů a potom formátuje data a zapisuje *je do paměti, na kterou* ukazuje *vyrovnávací paměť*. Funkce **vsnprintf** vždy zapisuje ukončovací znak null, i když zkrátí výstup. Při použití **_vsnprintf** a **_vsnwprintf**se vyrovnávací paměť ukončí jenom v případě, že je na konci místnost (tj. Pokud počet znaků, které se mají zapisovat, je menší než *počet*).

> [!IMPORTANT]
> Chcete-li zabránit určitým druhům rizik zabezpečení, zajistěte, aby *Formát* nebyl uživatelem definovaným řetězcem. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

> [!NOTE]
> Chcete-li zajistit, aby při volání **_vsnprintf**, **_vsnprintf_l**, **_vsnwprintf** a **_vsnwprintf_l**existoval prostor pro ukončující hodnotu null, ujistěte se, že je *počet* striktně menší než délka vyrovnávací paměti a inicializuje vyrovnávací paměť na hodnota null před voláním funkce.
>
> Vzhledem k tomu, že **vsnprintf** vždy zapisuje ukončující hodnotu null, parametr *Count* může být stejný jako velikost vyrovnávací paměti.

Od UCRT v prostředí Visual Studio 2015 a Windows 10 se **vsnprintf** už neshoduje s **_vsnprintf**. Funkce **vsnprintf** je v souladu s C99 standardem; **_vnsprintf** se zachovává kvůli zpětné kompatibilitě se starším kódem sady Visual Studio.

Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí vlákna.

V C++nástroji mají tyto funkce přetížení šablony, které vyvolávají novější a zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf**|**_vsnprintf**|**_vsnprintf**|**_vsnwprintf**|
|**_vsntprintf_l**|**_vsnprintf_l**|**_vsnprintf_l**|**_vsnwprintf_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|-------------|---------------------------|-------------------------------|
|**vsnprintf**, **_vsnprintf**, **_vsnprintf_l**|\<stdio.h>|\<stdio. h > nebo \<cstdio >|
|**_vsnwprintf**, **_vsnwprintf_l**|\<stdio. h > nebo \<WCHAR. h >|\<stdio. h >, \<WCHAR. h >, \<cstdio > nebo \<cwchar >|

Funkce **_vsnprintf**, **_vsnprintf_l**, **_vsnwprintf** a **_vsnwprintf_l** jsou specifické pro společnost Microsoft. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_vsnwprintf.c
// compile by using: cl /W3 crt_vsnwprintf.c

// To turn off error C4996, define this symbol:
#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>
#include <wtypes.h>

#define BUFFCOUNT (10)

void FormatOutput(LPCWSTR formatstring, ...)
{
    int nSize = 0;
    wchar_t buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    // Note: _vsnwprintf is deprecated; consider vsnwprintf_s instead
    nSize = _vsnwprintf(buff, BUFFCOUNT - 1, formatstring, args); // C4996
    wprintf(L"nSize: %d, buff: %ls\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput(L"%ls %ls", L"Hi", L"there");
    FormatOutput(L"%ls %ls", L"Hi", L"there!");
    FormatOutput(L"%ls %ls", L"Hi", L"there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

Chování se mění, pokud místo toho použijete vsnprintf spolu s parametry s úzkým řetězcem. Parametr *Count* může být celá velikost vyrovnávací paměti a vrácená hodnota je počet znaků, které byly zapsány, pokud byl *počet* dostatečně velký:

## <a name="example"></a>Příklad

```C
// crt_vsnprintf.c
// compile by using: cl /W4 crt_vsnprintf.c
#include <stdio.h>
#include <stdarg.h> // for va_list, va_start
#include <string.h> // for memset

#define BUFFCOUNT (10)

void FormatOutput(char* formatstring, ...)
{
    int nSize = 0;
    char buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    nSize = vsnprintf(buff, sizeof(buff), formatstring, args);
    printf("nSize: %d, buff: %s\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput("%s %s", "Hi", "there");   //  8 chars + null
    FormatOutput("%s %s", "Hi", "there!");  //  9 chars + null
    FormatOutput("%s %s", "Hi", "there!!"); // 10 chars + null
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: 10, buff: Hi there!
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
[Syntaxe specifikace formátu: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
