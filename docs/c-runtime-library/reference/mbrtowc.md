---
title: "mbrtowc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: mbrtowc
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords: mbrtowc
dev_langs: C++
helpviewer_keywords: mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: afbc17fbe93fdead069ca89ebbaf0eee400cd746
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mbrtowc"></a>mbrtowc
Převeďte vícebajtových znaků v aktuální národní prostředí ekvivalentní široká znaková s schopnosti produktu restartování uprostřed vícebajtových znaků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t mbrtowc(  
   wchar_t *wchar,  
   const char *mbchar,  
   size_t count,  
   mbstate_t *mbstate  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wchar`  
 Adresa široká znaková řetězec převedený široká znaková (typ `wchar_t`). Tato hodnota může být ukazatele null, pokud žádné návratový široká znaková se vyžaduje.  
  
 `mbchar`  
 Adresa pořadí bajtů (vícebajtových znaků).  
  
 `count`  
 Počet bajtů ke kontrole.  
  
 `mbstate`  
 Ukazatel na převod stavu objektu. Pokud je tato hodnota ukazatele null, funkce používá objekt statické vnitřní převod stavu. Protože interní `mbstate_t` objekt není bezpečné pro přístup z více vláken, doporučujeme, aby vždy předáte vlastní `mbstate` argument.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jedna z následujících hodnot:  
  
 0  
 Další `count` nebo méně bajtů dokončení vícebajtových znaků, který představuje hodnotu null široké znak, který je uložen v `wchar`, pokud `wchar` není nulový ukazatel.  
  
 1 `count`(včetně)  
 Další `count` nebo méně bajtů dokončení platný vícebajtových znaků. Hodnota vrácená je počet bajtů, která dokončí vícebajtových znaků. Široká znaková ekvivalentní je uložen v `wchar`, pokud `wchar` není nulový ukazatel.  
  
 size_t (–) (-1)  
 Došlo k chybě kódování. Další `count` nebo méně bajtů nepřispívají k dokončení a platné vícebajtových znaků. V takovém případě `errno` je nastavena na eilseq – a stav převodu posunutí v `mbstate` není zadáno.  
  
 size_t (–) -(2)  
 Další `count` bajtů přispívat do neúplné ale potenciálně platný vícebajtových znaků a všechny `count` bajtů byly zpracovány. Žádná hodnota je uložena v `wchar`, ale `mbstate` se aktualizuje na restartovat funkce.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `mbchar` je ukazatel s hodnotou null, je ekvivalentní volání funkce:  
  
 `mbrtowc(NULL, "", 1, &mbstate)`  
  
 V tomto případě hodnotu argumenty `wchar` a `count` jsou ignorovány.  
  
 Pokud `mbchar` není ukazatel s hodnotou null, funkce prozkoumá `count` bajtů z `mbchar` určete požadovaný počet bajtů, které jsou nutné k dokončení další vícebajtových znaků. Pokud další znak je platný, odpovídající vícebajtových znaků je uložen v `wchar` Pokud není nulový ukazatel. Pokud je znak odpovídající celý null znak, výsledný stav `mbstate` je počáteční převod stavu.  
  
 `mbrtowc` Funkce se liší od [mbtowc –, _mbtowc_l –](../../c-runtime-library/reference/mbtowc-mbtowc-l.md) podle jeho restartability. Stav převodu je uložený ve `mbstate` pro následující volání stejné nebo jiné funkce nabízet možnost restartování. Výsledky nejsou definovány při kombinování použití funkce nonrestartable a nabízet možnost restartování.  Například by měla použít aplikace `wcsrlen` místo `wcslen` Pokud následných volání `wcsrtombs` se používá místo `wcstombs`.  
  
## <a name="example"></a>Příklad  
 Převede na jeho široká znaková ekvivalentní vícebajtových znaků.  
  
```  
// crt_mbrtowc.cpp  
  
#include <stdio.h>  
#include <mbctype.h>  
#include <string.h>  
#include <locale.h>  
#include <wchar.h>  
  
#define BUF_SIZE 100  
  
int Sample(char* szIn, wchar_t* wcOut, int nMax)  
{  
    mbstate_t   state = {0}; // Initial state  
    size_t      nConvResult,   
                nmbLen = 0,  
                nwcLen = 0;  
    wchar_t*    wcCur = wcOut;  
    wchar_t*    wcEnd = wcCur + nMax;  
    const char* mbCur = szIn;  
    const char* mbEnd = mbCur + strlen(mbCur) + 1;  
    char*       szLocal;  
  
    // Sets all locale to French_Canada.1252  
    szLocal = setlocale(LC_ALL, "French_Canada.1252");  
    if (!szLocal)  
    {  
        printf("The fuction setlocale(LC_ALL, \"French_Canada.1252\") failed!\n");  
        return 1;  
    }  
  
    printf("Locale set to: \"%s\"\n", szLocal);  
  
    // Sets the code page associated current locale's code page  
    // from a previous call to setlocale.  
    if (_setmbcp(_MB_CP_SBCS) == -1)  
    {  
        printf("The fuction _setmbcp(_MB_CP_SBCS) failed!");  
        return 1;  
    }  
  
    while ((mbCur < mbEnd) && (wcCur < wcEnd))  
    {  
        //  
        nConvResult = mbrtowc(wcCur, mbCur, 1, &state);  
        switch (nConvResult)  
        {  
            case 0:  
            {  // done  
                printf("Conversion succeeded!\nMultibyte String: ");  
                printf(szIn);  
                printf("\nWC String: ");  
                wprintf(wcOut);  
                printf("\n");  
                mbCur = mbEnd;  
                break;  
            }  
  
            case -1:  
            {  // encoding error  
                printf("The call to mbrtowc has detected an encoding error.\n");  
                mbCur = mbEnd;  
                break;  
            }  
  
            case -2:  
            {  // incomplete character  
                if   (!mbsinit(&state))  
                {  
                    printf("Currently in middle of mb conversion, state = %x\n", state);  
                    // state will contain data regarding lead byte of mb character  
                }  
  
                ++nmbLen;  
                ++mbCur;  
                break;  
            }  
  
            default:  
            {  
                if   (nConvResult > 2) // The multibyte should never be larger than 2  
                {  
                    printf("Error: The size of the converted multibyte is %d.\n", nConvResult);  
                }  
  
                ++nmbLen;  
                ++nwcLen;  
                ++wcCur;  
                ++mbCur;  
            break;  
            }  
        }  
    }  
  
   return 0;  
}  
  
int main(int argc, char* argv[])  
{  
    char    mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";  
    wchar_t wcBuf[BUF_SIZE] = {L''};  
  
    return Sample(mbBuf, wcBuf, BUF_SIZE);  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
Locale set to: "French_Canada.1252"  
Conversion succeeded!  
Multibyte String: AaBbCcÜïα∩≡xXyYzZ  
WC String: AaBbCcÜïα∩≡xXyYzZ  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`mbrtowc`|\<wchar.h >|  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)