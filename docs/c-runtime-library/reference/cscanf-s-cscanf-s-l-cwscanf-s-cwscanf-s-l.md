---
title: "_cscanf_s –, _cscanf_s_l –, _cwscanf_s –, _cwscanf_s_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cwscanf_s_l
- _cwscanf_s
- _cscanf_s
- _cscanf_s_l
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
- cscanf_s
- cscanf_s_l
- cwscanf_s
- _cwscanf_s
- _tcscanf_s
- _cscanf_s
- _cwscanf_s_l
- _cscanf_s_l
- cwscanf_s_l
- _tcscanf_s_l
- tcscanf_s
- tcscanf_s_l
dev_langs: C++
helpviewer_keywords:
- cscanf_s function
- _cwscanf_s_l function
- tcscanf_s function
- console [C++], reading from
- _cscanf_s function
- data [C++], reading from the console
- cwscanf_s function
- _tcscanf_s_l function
- _cscanf_s_l function
- cscanf_s_l function
- cwscanf_s_l function
- reading data [C++], from the console
- _cwscanf_s function
- _tcscanf_s function
- tcscanf_s_l function
ms.assetid: 9ccab74d-916f-42a6-93d8-920525efdf4b
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cf20837a7abc336f120f031636a67264549e8d11
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cscanfs-cscanfsl-cwscanfs-cwscanfsl"></a>_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l
Čtení formátovaných dat z konzoly. Tyto další zabezpečené verzích [_cscanf –, _cscanf_l –, _cwscanf –, _cwscanf_l –](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _cscanf_s(   
   const char *format [,  
   argument] ...   
);  
int _cscanf_s_l(   
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _cwscanf_s(   
   const wchar_t *format [,  
   argument] ...   
);  
int _cwscanf_s_l(   
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `format`  
 Řetězec řízení formátu  
  
 `argument`  
 Volitelné parametry.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet polí, které byly úspěšně převést a přiřadit. Návratová hodnota nezahrnuje pole, které byly pro čtení, ale není přiřazen. Vrácená hodnota je `EOF` pro pokus o čtení na konci souboru. Tato situace může nastat, když vstup z klávesnice přesměrována na úrovni příkazového řádku operačního systému. Vrácená hodnota 0 znamená, že byly přiřazené žádné pole.  
  
 Tyto funkce ověřit jejich parametrů. Pokud `format` je ukazatel s hodnotou null, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `EOF` a `errno` je nastaven na `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 `_cscanf_s` Funkce čte data přímo z konzoly do umístění určeného vlastností `argument`. [_Getche –](../../c-runtime-library/reference/getch-getwch.md) funkce slouží k načtení znaků. Všechny volitelné parametry musí být ukazatel na proměnnou s typem, který odpovídá specifikátor typu v `format`. Ovládací prvky formátu výklad vstupní pole a má stejnou tvoří a fungovat jako `format` parametr pro [scanf_s –](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) funkce. Při `_cscanf_s` normálně vrátí vstupní znak ji není provést, pokud byl posledním volání do `_ungetch`.  
  
 Jako další bezpečné verze funkcí v `scanf` rodiny, `_cscanf_s` a `_cswscanf_s` vyžadovat velikosti argumenty pro znaky pole typu `c`, `C`, `s`, `S`, a `[`. Další informace najdete v tématu [specifikace šířky scanf](../../c-runtime-library/scanf-width-specification.md).  
  
> [!NOTE]
>  Parametr velikosti je typu `unsigned`, nikoli `size_t`.  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcscanf_s`|`_cscanf_s`|`_cscanf_s`|`_cwscanf_s`|  
|`_tcscanf_s_l`|`_cscanf_s_l`|`_cscanf_s_l`|`_cwscanf_s_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_cscanf_s`,`_cscanf_s_l`|\<conio.h >|  
|`_cwscanf_s`, `_cwscanf_s_l`|\<conio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_cscanf_s.c  
// compile with: /c  
/* This program prompts for a string  
 * and uses _cscanf_s to read in the response.  
 * Then _cscanf_s returns the number of items  
 * matched, and the program displays that number.  
 */  
  
#include <stdio.h>  
#include <conio.h>  
  
int main( void )  
{  
   int result, n[3];  
   int i;  
  
   result = _cscanf_s( "%i %i %i", &n[0], &n[1], &n[2] );  
   _cprintf_s( "\r\nYou entered " );  
   for( i=0; i<result; i++ )  
      _cprintf_s( "%i ", n[i] );  
   _cprintf_s( "\r\n" );  
}  
```  
  
## <a name="input"></a>Vstup  
  
```  
1 2 3  
```  
  
## <a name="output"></a>Výstup  
  
```  
You entered 1 2 3  
```  
  
## <a name="see-also"></a>Viz také  
 [I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)   
 [_cprintf –, _cprintf_l –, _cwprintf –, _cwprintf_l –](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fscanf_s –, _fscanf_s_l –, fwscanf_s –, _fwscanf_s_l –](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)   
 [scanf_s –, _scanf_s_l –, wscanf_s –, _wscanf_s_l –](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [sscanf_s –, _sscanf_s_l –, swscanf_s –, _swscanf_s_l –](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)