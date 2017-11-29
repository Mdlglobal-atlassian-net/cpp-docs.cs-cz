---
title: "vsnprintf –, _vsnprintf –, _vsnprintf_l –, _vsnwprintf –, _vsnwprintf_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
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
dev_langs: C++
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
caps.latest.revision: "35"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4850299b43b805c93136a59d5ee227e8bf79d2dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vsnprintf-vsnprintf-vsnprintfl-vsnwprintf-vsnwprintfl"></a>vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l
Zapíše formátovaný výstup pomocí ukazatele na seznam argumentů. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [vsnprintf_s –, _vsnprintf_s –, _vsnprintf_s_l –, _vsnwprintf_s –, _vsnwprintf_s_l –](../../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Umístění úložiště pro výstup.  
  
 `count`  
 Maximální počet znaků k zápisu.  
  
 `format`  
 Specifikace formátu.  
  
 `argptr`  
 Ukazatel na seznam argumentů.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
 Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 `vsnprintf` Funkce vrátí počet znaků zapsána, není počítání ukončující znak hodnoty null. Pokud velikost vyrovnávací paměti určuje `count` není dostatečně velký pro obsahovat výstup určeného `format` a `argptr`, vrátí hodnotu, která `vsnprintf` je počet znaků, které by byla zapsána, pokud není počítání znak hodnoty null `count` byly dostatečně velké. Pokud je vrácená hodnota je větší než `count` – 1, byl zkrácen výstup. Vrácená hodnota -1 označuje, že kódování došlo k chybě.  
  
 Obě `_vsnprintf` a `_vsnwprintf` funkce vrátí počet znaků, pokud počet znaků pro zápis je menší než nebo rovna hodnotě `count`; Pokud je větší než počet znaků k zápisu `count`, tyto funkce vrátí hodnotu -1 indikující, že byl zkrácen výstup.  
  
 Hodnota vrácená těmito funkcemi nezahrnuje ukončující null, jeden je zapsán, nebo ne. Když `count` rovná nule, je počet znaků, které by zápis funkce, není včetně všech ukončující null vrácená hodnota. Můžete použít tento výsledek přidělit velikost vyrovnávací paměti pro řetězce a jeho ukončující null a zavolejte funkci znovu k vyplnění vyrovnávací paměti.  
  
 Pokud `format` je `NULL`, nebo pokud `buffer` má hodnotu NULL a `count` není rovná nule, tato funkce má neplatný parametr obslužná rutina volat, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte `errno` k `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí má ukazatel na seznam argumentů, pak formátů data a zapíše až `count` znaků do paměti na kterou odkazuje `buffer`. `vsnprintf` Funkce vždy zapíše zakončením hodnotu null, i v případě, že se zkrátí výstup. Při použití `_vsnprintf` a `_vsnwprintf`, vyrovnávací paměť se null ukončí pouze v případě, že je na konci prostor (tj. Pokud počet znaků pro zápis je menší než `count`).  
  
> [!IMPORTANT]
>  Pokud chcete zabránit určité druhy rizika zabezpečení, zajistěte, aby `format` není řetězec definovaný uživatelem. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
> [!NOTE]
>  Aby bylo zajištěno, že místo pro ukončující null při volání metody `_vsnprintf`, `_vsnprintf_l`, `_vsnwprintf` a `_vsnwprintf_l`, ujistěte se, který `count` je striktně menší než délka vyrovnávací paměti a inicializace vyrovnávací paměti pro hodnotu null. před voláním funkce.  
>   
>  Protože `vsnprintf` vždy zapíše ukončující null, `count` parametr může být roven velikost vyrovnávací paměti.  
  
 Počínaje UCRT v sadě Visual Studio 2015 a Windows 10, `vsnprintf` již není stejný jako `_vsnprintf`. `vsnprintf` Funkce v souladu se standardem C99; `_vnsprintf` se zachovává kvůli zpětné kompatibilitě se starším kódu v sadě Visual Studio.  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.  
  
 V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vsntprintf`|`_vsnprintf`|`_vsnprintf`|`_vsnwprintf`|  
|`_vsntprintf_l`|`_vsnprintf_l`|`_vsnprintf_l`|`_vsnwprintf_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|  
|-------------|---------------------------|-------------------------------|  
|`vsnprintf`, `_vsnprintf`, `_vsnprintf_l`|\<stdio.h >|\<stdio.h > nebo \<cstdio – >|  
|`_vsnwprintf`, `_vsnwprintf_l`|\<stdio.h > nebo \<wchar.h >|\<stdio.h >, \<wchar.h >, \<cstdio – >, nebo \<cwchar – >|  
  
 `_vsnprintf`, `_vsnprintf_l`, `_vsnwprintf` a `_vsnwprintf_l` funkce se konkrétní společnosti Microsoft. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
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
  
 Změny chování, pokud místo toho použít vsnprintf – spolu s parametry úzké řetězce. `count` Parametr může být celý velikost vyrovnávací paměti a počet znaků, které by byla zapsána, pokud je vrácená hodnota `count` byla dostatečně velké na to:  
  
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
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [vprintf – funkce](../../c-runtime-library/vprintf-functions.md)   
 [Syntaxe specifikace formátu: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [fprintf, _fprintf_l –, fwprintf –, _fwprintf_l –](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l –, wprintf, _wprintf_l –](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg –, va_copy –, va_end –, va_start –](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)