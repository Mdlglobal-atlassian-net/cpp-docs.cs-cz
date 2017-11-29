---
title: "_putch_nolock –, _putwch_nolock – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _putwch_nolock
- _putch_nolock
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
- _putch_nolock
- _puttch_nolock
- putch_nolock
- putwch_nolock
- _putwch_nolock
dev_langs: C++
helpviewer_keywords:
- putwch_nolock function
- puttch_nolock function
- characters, writing
- putch_nolock function
- _putch_nolock function
- _puttch_nolock function
- console, writing characters to
- _putwch_nolock function
ms.assetid: edbc811d-bac6-47fa-a872-fe4f3a1590b0
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 75da1fcf2596bc8ab65c6fe2403c8397170a22b1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="putchnolock-putwchnolock"></a>_putch_nolock, _putwch_nolock
Zapíše znak ke konzole bez blokování vlákno.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int _putch_nolock(  
int c  
);  
wint_t _putwch_nolock(  
wchar_t c  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *c*  
 Znak, který má být výstup.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí *c* v případě úspěchu. Pokud **_putch_nolock –** nezdaří, vrátí **EOF**; Pokud **_putwch_nolock –** nezdaří, vrátí **weof –**.  
  
## <a name="remarks"></a>Poznámky  
 **_putch_nolock –** a **_putwch_nolock –** jsou stejné jako **_putch –** a **_putwch –**, s tím rozdílem, že nejsou chráněny před rušení další vlákna. Může být rychlejší, protože nevznikají nároky na uzamčení jiná vlákna. Tyto funkce lze používejte pouze v kontextu vláken jako je například aplikace nebo kde oboru volání již zpracovává izolace přístup z více vláken.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|**_puttch_nolock –**|**_putch_nolock –**|**_putch_nolock –**|**_putwch_nolock –**|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|**_putch_nolock –**|\<conio.h >|  
|**_putwch_nolock –**|\<conio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)   
 [_cprintf –, _cprintf_l –, _cwprintf –, _cwprintf_l –](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [_getch –, _getwch –](../../c-runtime-library/reference/getch-getwch.md)