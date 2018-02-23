---
title: "wcstombs_s –, _wcstombs_s_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wcstombs_s_l
- wcstombs_s
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
f1_keywords:
- wcstombs_s
- _wcstombs_s_l
dev_langs:
- C++
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 863f6dc5b1c7a41145607e8f8ba83466324dac07
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="wcstombss-wcstombssl"></a>wcstombs_s, _wcstombs_s_l

Převede posloupnost široké znaky na odpovídající posloupnost více-bajtové znaky. Verzi [wcstombs –, _wcstombs_l –](../../c-runtime-library/reference/wcstombs-wcstombs-l.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count   
);  

errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  

template <size_t size>  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  

template <size_t size>  
errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  

[out] *pReturnValue*  
Počet znaků převést.  
  
[out] *mbstr*  
Adresa vyrovnávací paměti pro výsledný řetězec převedený vícebajtových znaků.  
  
[v] *sizeInBytes*  
Velikost v bajtech *mbstr* vyrovnávací paměti.  
  
[v] *wcstr*  
Odkazuje na široká znaková řetězec, který má být převeden.  
  
[v] *počet*  
Maximální počet bajtů pro ukládání *mbstr* vyrovnávací paměti není včetně ukončující znak hodnoty null, nebo [_truncate –](../../c-runtime-library/truncate.md).  
  
[v] *národní prostředí*  
Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  

Nula v případě úspěchu, kód chyby při selhání.  
  
|Chybový stav|Vrátí hodnotu a `errno`|  
|---------------------|------------------------------|  
|*mbstr* je `NULL` a *sizeInBytes* > 0|`EINVAL`|  
|*wcstr* je `NULL`|`EINVAL`|  
|Cílová vyrovnávací paměť je příliš malá tak, aby obsahovala převedený řetězec (Pokud *počet* je `_TRUNCATE`; viz poznámky níže)|`ERANGE`|  
  
Pokud dojde k některé z těchto podmínek, jak je popsáno v je vyvolána výjimka neplatný parametr [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno provádění pokračovat, funkce vrátí kód chyby a nastaví `errno` , které je uvedené v tabulce.  
  
## <a name="remarks"></a>Poznámky  

`wcstombs_s` Funkce převede řetězec z široké znaky, na kterou odkazuje *wcstr* do více-bajtové znaky, které jsou uložené ve vyrovnávací paměti, na kterou odkazuje *mbstr*. Převod bude pokračovat pro jednotlivé znaky, dokud je splněna jedna z těchto podmínek:  
  
-   Vyskytl se null široká znaková  
  
-   Vyskytl se široká znaková, kterou nelze převést  
  
-   Počet bajtů, které jsou uložené v *mbstr* vyrovnávací paměti je rovno *počet*.  
  
Cílový řetězec je vždy ukončený hodnotou null (i v případě chyby).  
  
Pokud *počet* je speciální hodnota [_truncate –](../../c-runtime-library/truncate.md), pak `wcstombs_s` převede co nejvíc řetězec jako bude začlenit do cílové vyrovnávací paměti, a přesto nechat místo pro zakončením hodnotu null. Pokud se zkrátí řetězec, je vrácenou hodnotu `STRUNCATE`, a převod je považovat za úspěšné.  
  
Pokud `wcstombs_s` úspěšně převede zdrojový řetězec, uloží je velikost v bajtech převedený řetězec, včetně null ukončení do `*pReturnValue` (zadat *pReturnValue* není `NULL`). K tomu dojde i v případě *mbstr* argument je `NULL` a poskytuje způsob, jak určit velikost požadované vyrovnávací paměti. Všimněte si, že pokud *mbstr* je `NULL`, *počet* je ignorována.  
  
Pokud `wcstombs_s` zaznamená široká znaková nelze převést na vícebajtových znaků, uloží je 0 `*pReturnValue`, nastaví cílové vyrovnávací paměti na prázdný řetězec, nastaví `errno` k `EILSEQ`a vrátí `EILSEQ`.  
  
Pokud daná pořadí na kterou odkazuje *wcstr* a *mbstr* překrývají, chování `wcstombs_s` není definován.  
  
> [!IMPORTANT]
>  Ujistěte se, že *wcstr* a *mbstr* se nepřekrývají a že *počet* správně odpovídá počtu široké znaky převést.  
  
`wcstombs_s` používá aktuální národní prostředí pro chování všech závislých na národním prostředí; `_wcstombs_s_l` je stejný jako `wcstombs` s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`wcstombs_s`|\<stdlib.h>|  
  
Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  

Tento program znázorňuje chování `wcstombs_s` funkce.  
  
```C  
// crt_wcstombs_s.c  
// This example converts a wide character  
// string to a multibyte character string.  
#include <stdio.h>  
#include <stdlib.h>  
#include <assert.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t   i;  
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t*pWCBuffer = L"Hello, world.";  
  
    printf( "Convert wide-character string:\n" );  
  
    // Conversion  
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,   
               pWCBuffer, (size_t)BUFFER_SIZE );  
  
    // Output  
    printf("   Characters converted: %u\n", i);  
    printf("    Multibyte character: %s\n\n",  
     pMBBuffer );  
  
    // Free multibyte character buffer  
    if (pMBBuffer)  
    {  
    free(pMBBuffer);  
    }  
}  
```  
  
```Output  
Convert wide-character string:  
   Characters converted: 14  
    Multibyte character: Hello, world.  
```  
  
## <a name="see-also"></a>Viz také  

[Převod dat](../../c-runtime-library/data-conversion.md)   
[Národní prostředí](../../c-runtime-library/locale.md)   
[_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
[mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
[mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
[wctomb_s, _wctomb_s_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)   
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)