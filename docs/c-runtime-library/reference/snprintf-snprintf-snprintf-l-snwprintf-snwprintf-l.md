---
title: "snprintf –, _snprintf –, _snprintf_l –, _snwprintf –, _snwprintf_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _snwprintf
- _snprintf
- _snprintf_l
- _snwprintf_l
- snprintf
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
- _snprintf
- snprintf_l
- snwprintf_l
- sntprintf
- snprintf
- _sntprintf
- _sntprintf_l
- sntprintf_l
- snwprintf
- _snprintf_l
- _snwprintf
- _snwprintf_l
dev_langs: C++
helpviewer_keywords:
- snwprintf_l function
- sntprintf_l function
- snprintf_l function
- _snwprintf_l function
- _sntprintf_l function
- _snwprintf function
- _snprintf function
- _sntprintf function
- _snprintf_l function
- snwprintf function
- snprintf function
- sntprintf function
- formatted text [C++]
ms.assetid: 5976c9c8-876e-4ac9-a515-39f3f7fd0925
caps.latest.revision: "35"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0441f2debf2e030702727c92a6e27bea63cb0564
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="snprintf-snprintf-snprintfl-snwprintf-snwprintfl"></a>snprintf –, _snprintf –, _snprintf_l –, _snwprintf –, _snwprintf_l –
Zapisuje formátovaná data do řetězce. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_snprintf_s –, _snprintf_s_l –, _snwprintf_s –, _snwprintf_s_l –](../../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int snprintf(  
   char *buffer,  
   size_t count,  
   const char *format [,  
   argument] ...   
);  
int _snprintf(  
   char *buffer,  
   size_t count,  
   const char *format [,  
   argument] ...   
);  
int _snprintf_l(  
   char *buffer,  
   size_t count,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _snwprintf(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format [,  
   argument] ...   
);  
int _snwprintf_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
template <size_t size>  
int _snprintf(  
   char (&buffer)[size],  
   size_t count,  
   const char *format [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _snprintf_l(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _snwprintf(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _snwprintf_l(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Umístění úložiště pro výstup  
  
 `count`  
 Maximální počet znaků, které se mají uložit  
  
 `format`  
 Řetězec řízení formátu  
  
 `argument`  
 Volitelné argumenty  
  
 `locale`  
 Národní prostředí, které se má použít  
  
 Další informace najdete v tématu [syntaxe specifikace formátu: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Umožní `len` mít délku řetězce formátovaných dat, není včetně ukončující hodnotu null. Obě `len` a `count` jsou v bajtech pro `snprintf` a `_snprintf`, celý znaků pro `_snwprintf`.  
  
 Pro všechny funkce Pokud `len`  <  `count`, `len` znaky jsou uložené v `buffer`, zakončením null se připojí, a `len` je vrácen.  
  
 `snprintf` Funkce zkrátí výstup při `len` je větší než nebo rovno `count`, tím, že umístíte zakončením null v `buffer[count-1]`. Vrácená hodnota `len`, počet znaků, které by byly výstup v případě `count` byla dostatečně velké na to. `snprintf` Funkce vrací záporná, pokud dojde k chybě kódování.  
  
 Pro všechny funkce jiné než `snprintf`, pokud `len`  =  `count`, `len` znaky jsou uložené v `buffer`, je připojeno žádné null ukončení, a `len` je vrácen. Pokud `len`  >  `count`, `count` znaky jsou uložené v `buffer`, je připojeno žádné ukončení hodnotu null a je vrácena záporná hodnota.  
  
 Pokud `buffer` je ukazatel s hodnotou null a `count` rovná nule, `len` se vrátí jako počet znaků požadovaných k formátování výstupu, není včetně ukončující hodnotu null. Pro úspěšné volání se stejným `argument` a `locale` parametry, přidělit vyrovnávací paměť podržíte alespoň `len` + 1 znaků.  
  
 Pokud `buffer` je ukazatel s hodnotou null a `count` je nenulové hodnoty, nebo pokud `format` je ukazatel s hodnotou null, je volána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte `errno` k `EINVAL`.  
  
 Informace o těchto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `snprintf` Funkce a `_snprintf` rodiny formátu funkce a úložiště `count` nebo méně znaků v `buffer`. `snprintf` Vždycky uložena ukončující prázdný znak, zkrátit výstup v případě potřeby. `_snprintf` Řady funkcí pouze připojí ukončující znak hodnoty null, pokud je délka formátovaný řetězec striktně menší než `count` znaků. Každý `argument` (pokud existuje) je převeden a je výstup podle odpovídající specifikaci formátu v `format`. Formát obsahuje obyčejnou znaky a má stejné tvoří a fungovat jako `format` argument pro [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.  
  
> [!IMPORTANT]
>  Ujistěte se, že `format` není řetězec definovaný uživatelem. Protože `_snprintf` funkce nezaručují NULL ukončení – zejména, pokud je návratovou hodnotu `count`– zajistěte, aby se následuje kód, který přidá null ukončení. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 Počínaje UCRT v sadě Visual Studio 2015 a Windows 10, `snprintf` již není stejný jako `_snprintf`. `snprintf` Chování funkce je nyní C99 standard kompatibilní.  
  
 `_snwprintf`široká charakterová verze `_snprintf`; ukazatel argumenty, které mají `_snwprintf` jsou široká charakterová řetězce. Detekce chyb v kódování `_snwprintf` může lišit od v `_snprintf`. `_snwprintf`, stejně jako `swprintf`, zapíše výstup na řetězec místo cílového typu `FILE`.  
  
 Verze tyto funkce, které mají `_l` příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.  
  
 V jazyce C++ mají tyto funkce přetížení šablon, která vyvolávají novější, lépe zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_sntprintf`|`_snprintf`|`_snprintf`|`_snwprintf`|  
|`_sntprintf_l`|`_snprintf_l`|`_snprintf_l`|`_snwprintf_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`snprintf`, `_snprintf`,  `_snprintf_l`|\<stdio.h >|  
|`_snwprintf`, `_snwprintf_l`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_snprintf.c  
// compile with: /W3  
#include <stdio.h>  
#include <stdlib.h>  
  
#if !defined(__cplusplus)  
typedef int bool;  
const bool true = 1;  
const bool false = 0;  
#endif  
  
#define FAIL 0 // change to 1 and see what happens  
  
int main(void)  
{  
   char buffer[200];  
   const static char s[] = "computer"  
#if FAIL  
"computercomputercomputercomputercomputercomputercomputercomputer"  
"computercomputercomputercomputercomputercomputercomputercomputer"  
"computercomputercomputercomputercomputercomputercomputercomputer"  
"computercomputercomputercomputercomputercomputercomputercomputer"  
#endif  
   ;  
   const char c = 'l';   
   const int i = 35;  
#if FAIL  
   const double fp = 1e300; // doesn't fit in the buffer  
#else  
   const double fp = 1.7320534;  
#endif  
   /* !subtract one to prevent "squeezing out" the terminal nul! */  
   const int bufferSize = sizeof(buffer)/sizeof(buffer[0]) - 1;  
   int bufferUsed = 0;  
   int bufferLeft = bufferSize - bufferUsed;  
   bool bSuccess = true;  
   buffer[0] = 0;  
  
   /* Format and print various data: */  
  
   if (bufferLeft > 0)  
   {  
      int perElementBufferUsed = _snprintf(&buffer[bufferUsed],   
      bufferLeft, "   String: %s\n", s ); // C4996  
      // Note: _snprintf is deprecated; consider _snprintf_s instead  
      if (bSuccess = (perElementBufferUsed >= 0))  
      {  
         bufferUsed += perElementBufferUsed;  
         bufferLeft -= perElementBufferUsed;  
         if (bufferLeft > 0)  
         {  
            int perElementBufferUsed = _snprintf(&buffer[bufferUsed],   
            bufferLeft, "   Character: %c\n", c ); // C4996  
            if (bSuccess = (perElementBufferUsed >= 0))  
            {  
               bufferUsed += perElementBufferUsed;  
               bufferLeft -= perElementBufferUsed;  
               if (bufferLeft > 0)  
               {  
                  int perElementBufferUsed = _snprintf(&buffer  
                  [bufferUsed], bufferLeft, "   Integer: %d\n", i ); // C4996  
                  if (bSuccess = (perElementBufferUsed >= 0))  
                  {  
                     bufferUsed += perElementBufferUsed;  
                     bufferLeft -= perElementBufferUsed;  
                     if (bufferLeft > 0)  
                     {  
                        int perElementBufferUsed = _snprintf(&buffer  
                        [bufferUsed], bufferLeft, "   Real: %f\n", fp ); // C4996  
                        if (bSuccess = (perElementBufferUsed >= 0))  
                        {  
                           bufferUsed += perElementBufferUsed;  
                        }  
                     }  
                  }  
               }  
            }  
         }  
      }  
   }  
  
   if (!bSuccess)  
   {  
      printf("%s\n", "failure");  
   }  
   else  
   {  
      /* !store nul because _snprintf doesn't necessarily (if the string   
       * fits without the terminal nul, but not with it)!  
       * bufferUsed might be as large as bufferSize, which normally is   
       * like going one element beyond a buffer, but in this case   
       * subtracted one from bufferSize, so we're ok.  
       */  
      buffer[bufferUsed] = 0;  
      printf( "Output:\n%s\ncharacter count = %d\n", buffer, bufferUsed );  
   }  
   return EXIT_SUCCESS;  
}  
```  
  
```Output  
Output:  
   String: computer  
   Character: l  
   Integer: 35  
   Real: 1.732053  
  
character count = 69  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [fprintf, _fprintf_l –, fwprintf –, _fwprintf_l –](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l –, wprintf, _wprintf_l –](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf, _scanf_l –, wscanf, _wscanf_l –](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf –, _sscanf_l –, swscanf –, _swscanf_l –](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf – funkce](../../c-runtime-library/vprintf-functions.md)