---
title: "mbrlen – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords: mbrlen
dev_langs: C++
helpviewer_keywords: mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d8276f716049915d1cd3b8c98074255d3327144c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mbrlen"></a>mbrlen
Určete počet bajtů, které jsou nutné k dokončení vícebajtových znaků v aktuální národní prostředí, pomocí funkce restartování uprostřed vícebajtových znaků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t mbrlen(  
   const char * str,  
   size_t count,  
   mbstate_t * mbstate  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Ukazatel na další bajtů, chcete-li prověřit řetězce vícebajtových znaků.  
  
 `count`  
 Maximální počet bajtů ke kontrole.  
  
 `mbstate`  
 Ukazatel na aktuální stav shift počáteční bajt `str`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jedna z následujících hodnot:  
  
 0  
 Další `count` nebo méně bajtů dokončení vícebajtových znaků, která představuje celou znak hodnoty null.  
  
 1 `count`(včetně)  
 Další `count` nebo méně bajtů dokončení platný vícebajtových znaků. Hodnota vrácená je počet bajtů, která dokončí vícebajtových znaků.  
  
 size_t (–) -(2)  
 Další `count` bajtů přispívat do neúplné ale potenciálně platný vícebajtových znaků a všechny `count` bajtů byly zpracovány.  
  
 size_t (–) (-1)  
 Došlo k chybě kódování. Další `count` nebo méně bajtů nepřispívají k dokončení a platné vícebajtových znaků. V takovém případě `errno` je nastavena na eilseq – a stav převodu v `mbstate` není zadáno.  
  
## <a name="remarks"></a>Poznámky  
 `mbrlen` Funkce zkontroluje maximálně `count` bajtů počínaje bajtů na kterou odkazuje `str` můžete určit počet bajtů, které jsou nutné k dokončení další vícebajtových znaků, včetně jakýchkoli pořadí shift. Ta je ekvivalentní volání `mbrtowc(NULL, str, count, &mbstate)` kde `mbstate` je buď zadaný uživatelem `mbstate_t` objekt nebo statické vnitřní objekt Poskytnutý knihovny.  
  
 `mbrlen` Funkce uloží a používá shift stav nekompletní vícebajtových znaků v `mbstate` parametr. Díky tomu `mbrlen` schopnosti produktu restartováním uprostřed vícebajtových znaků, pokud se potřeby zkoumání maximálně `count` bajtů. Pokud `mbstate` je ukazatel s hodnotou null, `mbrlen` používá interní statická `mbstate_t` objekt pro uložení stavu shift. Protože interní `mbstate_t` objekt není bezpečné pro přístup z více vláken, doporučujeme, abyste vždy přidělit a předat vlastní `mbstate` parametr.  
  
 `mbrlen` Funkce se liší od [_mbclen, mblen –, _mblen_l –](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md) podle jeho restartability. Stav posunutí je uložený ve `mbstate` pro následující volání stejné nebo jiné funkce nabízet možnost restartování. Výsledky nejsou definovány při kombinování použití funkce nonrestartable a nabízet možnost restartování.  Například by měla použít aplikace `wcsrlen` místo `wcslen` Pokud následných volání `wcsrtombs` se používá místo`wcstombs.`  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|Není k dispozici|Není k dispozici|`mbrlen`|Není k dispozici|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`mbrlen`|\<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak se výklad více-bajtové znaky závisí na aktuální stránce kódu a ukazuje, opětovné funkce `mbrlen`.  
  
```C  
// crt_mbrlen.c  
// Compile by using: cl crt_mbrlen.c  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
#include <locale.h>  
#include <wchar.h>  
  
size_t Example(const char * pStr)  
{  
    size_t      charLen = 0;  
    size_t      charCount = 0;  
    mbstate_t   mbState = {0};  
  
    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&  
            charLen != (size_t)-1)  
    {  
        if (charLen != (size_t)-2) // if complete mbcs char,  
        {  
            charCount++;  
        }  
    }   
    return (charCount);  
}   
  
int main( void )  
{  
    int         cp;  
    size_t      charCount = 0;  
    const char  *pSample =   
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";  
  
    cp = _getmbcp();  
    charCount = Example(pSample);  
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",   
        cp, pSample, charCount);  
  
    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale  
    _setmbcp(932); // and Japanese multibyte code page  
    cp = _getmbcp();  
    charCount = Example(pSample);  
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",   
        cp, pSample, charCount);  
}  
```  
  
```Output  
  
Code page: 0  
é╨éτé¬é╚: Shift-jis hiragana.  
Character count: 29  
  
Code page: 932  
????: Shift-jis hiragana.  
Character count: 25  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)