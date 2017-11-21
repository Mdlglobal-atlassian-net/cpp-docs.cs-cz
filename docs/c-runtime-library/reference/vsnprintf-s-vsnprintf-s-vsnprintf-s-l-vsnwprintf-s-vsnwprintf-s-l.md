---
title: "vsnprintf_s –, _vsnprintf_s –, _vsnprintf_s_l –, _vsnwprintf_s –, _vsnwprintf_s_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 741c3045781af5437c456028644678e5811f3378
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vsnprintfs-vsnprintfs-vsnprintfsl-vsnwprintfs-vsnwprintfsl"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l
Zapíše formátovaný výstup pomocí ukazatele na seznam argumentů. Toto jsou verze [vsnprintf –, _vsnprintf –, _vsnprintf_l –, _vsnwprintf –, _vsnwprintf_l –](../../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Umístění úložiště pro výstup.  
  
 `sizeOfBuffer`  
 Počet znaků parametru `buffer` pro výstup.  
  
 `count`  
 Maximální počet znaků k zápisu (nikoli včetně ukončující null), nebo [_truncate –](../../c-runtime-library/truncate.md).  
  
 `format`  
 Specifikace formátu.  
  
 `argptr`  
 Ukazatel na seznam argumentů.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
 Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 `vsnprintf_s`,`_vsnprintf_s` a `_vsnwprintf_s` vrátí počet znaků zapsána, pokud dojde k chybě výstup není včetně ukončující hodnotu null nebo záporná hodnota. Funkce `vsnprintf_s` je shodná s funkcí `_vsnprintf_s`. Funkce `vsnprintf_s` je součástí shody se standardem ANSI. Funkce `_vnsprintf` je zachována z důvodu zpětné kompatibility.  
  
 Pokud překročí úložiště potřebné pro uložení dat a ukončující null `sizeOfBuffer`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md), pokud `count` je [_truncate –](../../c-runtime-library/truncate.md), v takovém případě co nejvíc řetězec tak, jak se vejde `buffer` je zapsán a vrátí hodnotu -1. Pokud běh programu po obslužné rutině neplatného parametru pokračuje, nastaví tyto funkce parametr `buffer` na prázdný řetězec, parametr `errno` nastaví na hodnotu `ERANGE`a vrátí -1.  
  
 Pokud má parametr `buffer` nebo `format` hodnotu `NULL` nebo pokud je parametr `count` menší nebo roven nule, je vyvolána obslužná rutina neplatného parametru. Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí hodnotu -1.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`Condition`|Vrátí|`errno`|  
|-----------------|------------|-------------|  
|`buffer`je`NULL`|-1|`EINVAL`|  
|`format`je`NULL`|-1|`EINVAL`|  
|`count` <= 0|-1|`EINVAL`|  
|Parametr `sizeOfBuffer` je příliš malý (a parametr `count` != `_TRUNCATE`)|-1 (a parametr `buffer` nastaven na prázdný řetězec)|`ERANGE`|  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí přebírá ukazatel na seznam argumentů, potom provede formátování a zapíše počet znaků určených parametrem `count` do paměti, kam odkazuje parametr `buffer`, a připojí ukončující znak null.  
  
 Pokud `count` je [_truncate –](../../c-runtime-library/truncate.md), pak tyto funkce zápisu co nejvíc řetězce, který se vejde `buffer` a nechat místo pro ukončující hodnotu null. Pokud se do parametru `buffer` vejde celý řetězec (s ukončujícím znakem null), tyto funkce vrací počet zapsaných znaků (bez ukončujícího znaku null), v opačném případě tyto funkce vrátí -1, což označuje, že došlo ke zkrácení.  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.  
  
> [!IMPORTANT]
>  Ujistěte se, že `format` není řetězec definovaný uživatelem. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
> [!NOTE]
>  Abyste se ujistili, že existuje místo pro ukončující znak null, ověřte, že parametr `count` je menší než velikost vyrovnávací paměti nebo použijte konstantu `_TRUNCATE`.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vsntprintf_s`|`_vsnprintf_s`|`_vsnprintf_s`|`_vsnwprintf_s`|  
|`_vsntprintf_s_l`|`_vsnprintf_s_l`|`_vsnprintf_s_l`|`_vsnwprintf_s_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|  
|-------------|---------------------|----------------------|  
|`vsnprintf_s`|\<stdio.h > a \<stdarg.h >|\<VarArgs.h > *|  
|`_vsnprintf_s`, `_vsnprintf_s_l`|\<stdio.h > a \<stdarg.h >|\<VarArgs.h > *|  
|`_vsnwprintf_s`, `_vsnwprintf_s_l`|\<stdio.h > nebo \<wchar.h >, a \<stdarg.h >|\<VarArgs.h > *|  
  
 \*Vyžaduje se pro kompatibility V systému UNIX.  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
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
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [vprintf – funkce](../../c-runtime-library/vprintf-functions.md)   
 [fprintf, _fprintf_l –, fwprintf –, _fwprintf_l –](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l –, wprintf, _wprintf_l –](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg –, va_copy –, va_end –, va_start –](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)