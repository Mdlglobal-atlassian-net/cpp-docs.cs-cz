---
title: "vsscanf –, vswscanf – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- vsscanf
- vswscanf
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
- _vstscanf
- vsscanf
- vswscanf
dev_langs: C++
helpviewer_keywords:
- vswscanf function
- vsscanf function
ms.assetid: e96180f2-df46-423d-b4eb-0a49ab819bde
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 95446e1442f1df98dff5e1819e97c49c75209fda
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vsscanf-vswscanf"></a>vsscanf, vswscanf
Čtení formátovaných dat z řetězce. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [vsscanf_s vswscanf_s](../../c-runtime-library/reference/vsscanf-s-vswscanf-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int vsscanf(  
   const char *buffer,  
   const char *format,  
   va_list arglist  
);  
int vswscanf(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   va_list arglist  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Uložená data  
  
 `format`  
 Řetězec řízení formátu Další informace najdete v tématu [pole Specifikace formátu: funkce scanf a wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
 `arglist`  
 Seznam argumentů s proměnnou.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrátí počet polí, které jsou úspěšně převést a přiřadit; Návratová hodnota nezahrnuje pole, které byly pro čtení, ale není přiřazen. Vrácená hodnota 0 značí, že byly přiřazené žádné pole. Vrácená hodnota je `EOF` pro chybu nebo pokud je dosaženo konce řetězec před první převod.  
  
 Pokud `buffer` nebo `format` je `NULL` ukazatele, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte `errno` k `EINVAL`.  
  
 Informace o těchto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `vsscanf` Funkce Číst data z `buffer` do umístění, které jsou uvedeny v každém argumentu ve `arglist` seznam argumentů. Každý argument v seznamu musí být ukazatel do proměnné, která má typ, který odpovídá specifikátor typu v `format`. `format` Ovládací prvky argument výklad vstupní pole a má stejnou tvoří a fungovat jako `format` argument `scanf` funkce. Pokud kopírování probíhá mezi řetězce, které se překrývají, chování nedefinovaný.  
  
> [!IMPORTANT]
>  Při použití `vsscanf` číst řetězce, vždycky zadat šířku pro `%s` formátu (například `"%32s"` místo `"%s"`), jinak hodnota nesprávně naformátovanou vstup může způsobit přetečení vyrovnávací paměti.  
  
 `vswscanf`široká charakterová verze `vsscanf`; argumenty, které mají `vswscanf` jsou široká charakterová řetězce. `vsscanf`nezpracovává vícebajtové hexadecimálních znaků. `vswscanf`nezpracovává šestnáctkové kódování Unicode s plnou šířkou nebo znaků "kompatibility zóna". V opačném `vswscanf` a `vsscanf` chovají stejně jako.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vstscanf`|`vsscanf`|`vsscanf`|`vswscanf`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`vsscanf`|\<stdio.h >|  
|`vswscanf`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_vsscanf.c  
// compile with: /W3  
// This program uses vsscanf to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdarg.h>  
  
int call_vsscanf(char *tokenstring, char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vsscanf(tokenstring, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main( void )  
{  
    char  tokenstring[] = "15 12 14...";  
    char  s[81];  
    char  c;  
    int   i;  
    float fp;  
  
    // Input various data from tokenstring:  
    // max 80 character string:  
    call_vsscanf(tokenstring, "%80s", s);  
    call_vsscanf(tokenstring, "%c", &c);  
    call_vsscanf(tokenstring, "%d", &i);  
    call_vsscanf(tokenstring, "%f", &fp);  
  
    // Output the data read  
    printf("String    = %s\n", s);  
    printf("Character = %c\n", c);  
    printf("Integer:  = %d\n", i);  
    printf("Real:     = %f\n", fp);  
}  
```  
  
```Output  
String    = 15  
Character = 1  
Integer:  = 15  
Real:     = 15.000000  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [scanf, _scanf_l –, wscanf, _wscanf_l –](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf –, _sscanf_l –, swscanf –, _swscanf_l –](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vsscanf_s vswscanf_s](../../c-runtime-library/reference/vsscanf-s-vswscanf-s.md)