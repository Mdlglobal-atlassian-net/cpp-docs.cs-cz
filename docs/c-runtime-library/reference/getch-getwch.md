---
title: "_getch –, _getwch – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getch
- _getwch
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
- getwch
- _getch
- _getwch
dev_langs: C++
helpviewer_keywords:
- characters, getting from console
- getch function
- _getwch function
- console, reading from
- _getch function
- getwch function
ms.assetid: cc116be7-cff2-4274-970f-5e7b18ccc05c
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aee3ed86629689bc69b7f437d3e54339bf5a6710
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="getch-getwch"></a>_getch, _getwch
Získá znak z konzoly bez zobrazení.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _getch( void );  
wint_t _getwch( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí znak pro čtení. Neexistuje žádný návratový chyby.  
  
## <a name="remarks"></a>Poznámky  
 `_getch` a `_getwch` funkce číst jeden znak z konzole bez zobrazení znak. Žádná z těchto funkcí můžete použít ke čtení CTRL + C. Při čtení klíče funkce nebo klávesy se šipkami, každý funkce musí být volána dvakrát; Vrátí první volání 0 nebo 0xE0, a druhé volání vrátí kód skutečné klíče.  
  
 Tyto funkce Uzamknout volající vlákno a proto jsou bezpečné pro přístup z více vláken. Bez uzamčení verze najdete v tématu [_getch_nolock –, _getwch_nolock –](../../c-runtime-library/reference/getch-nolock-getwch-nolock.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_gettch`|`_getch`|`_getch`|`_getwch`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_getch`|\<conio.h >|  
|`_getwch`|\<conio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_getch.c  
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
      ch = _getch();  
      ch = toupper( ch );  
   } while( ch != 'Y' );  
  
   _putch( ch );  
   _putch( '\r' );    // Carriage return  
   _putch( '\n' );    // Line feed    
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
 [_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)