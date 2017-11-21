---
title: "_getch_nolock –, _getwch_nolock – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getwch_nolock
- _getch_nolock
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getch_nolock
- getwch_nolock
- getch_nolock
- _getwch_nolock
- _gettch_nolock
- gettch_nolock
dev_langs: C++
helpviewer_keywords:
- characters, getting from console
- _getwch_nolock function
- _getch_nolock function
- getwch_nolock function
- _gettch_nolock function
- console, reading from
- getch_nolock function
- gettch_nolock function
ms.assetid: 9d248546-26ca-482c-b0c6-55812a987e83
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bb903ad6ad61a7263559ad9dd3d47d85cb67e413
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="getchnolock-getwchnolock"></a>_getch_nolock, _getwch_nolock
Získá znak z konzole bez echo a bez blokování vlákno.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _getch_nolock( void );  
wint_t _getwch_nolock( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí znak pro čtení. Neexistuje žádný návratový chyby.  
  
## <a name="remarks"></a>Poznámky  
 `_getch_nolock`a `_getwch_nolock` jsou stejné jako `_getch` a `_getchw` s tím rozdílem, že jejich není chráněn z narušení jiná vlákna. Může být rychlejší, protože nevznikají nároky na uzamčení jiná vlákna. Tyto funkce lze používejte pouze v kontextu vláken jako je například aplikace nebo kde oboru volání již zpracovává izolace přístup z více vláken.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_gettch_nolock`|`_getch_nolock`|`_getch_nolock`|`_getwch_nolock`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_getch_nolock`|\<conio.h >|  
|`_getwch_nolock`|\<conio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_getch_nolock.c  
// compile with: /c  
// This program reads characters from  
// the keyboard until it receives a 'Y' or 'y'.  
  
#include <conio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
  
   _cputs( "Type 'Y' when finished typing keys: " );  
   do  
   {  
      ch = _getch_nolock();  
      ch = toupper( ch );  
   } while( ch != 'Y' );  
  
   _putch_nolock( ch );  
   _putch_nolock( '\r' );    // Carriage return  
   _putch_nolock( '\n' );    // Line feed  
}  
```  
  
```Input  
abcdefy
```
  
```Output  
Type 'Y' when finished typing keys: Y  
```  
  
## <a name="see-also"></a>Viz také  
 [I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)   
 [_getche –, _getwche –](../../c-runtime-library/reference/getche-getwche.md)   
 [_cgets –, _cgetws –](../../c-runtime-library/cgets-cgetws.md)   
 [getc, getwc –](../../c-runtime-library/reference/getc-getwc.md)   
 [_ungetch –, _ungetwch –, _ungetch_nolock –, _ungetwch_nolock –](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)