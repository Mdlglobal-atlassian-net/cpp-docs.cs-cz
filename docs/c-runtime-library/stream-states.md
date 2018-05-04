---
title: Stavy proudu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- streams, states
ms.assetid: 5f28c968-f132-403f-968c-8417ff315e52
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 418ed7c98523bf8944afcccc13a0e9020036940f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="stream-states"></a>Stavy proudu
Na následujícím obrázku jsou zobrazeny platné stavy a přechody stavu pro datový proud.  
  
 ![Datový proud](../c-runtime-library/media/stream.gif "datového proudu")  
  
 Každý kroužky označuje stabilního stavu. Každý řádek označuje přechodu, který může nastat v důsledku volání funkce, které funguje v datovém proudu. Pět skupin funkce může způsobit přechodů mezi stavy.  
  
 Funkce v první tři skupiny jsou deklarované v \<stdio.h >:  
  
-   Bajtů načíst funkce – [fgetc –](../c-runtime-library/reference/fgetc-fgetwc.md), [fgets –](../c-runtime-library/reference/fgets-fgetws.md), [fread –](../c-runtime-library/reference/fread.md), [fscanf –](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getc](../c-runtime-library/reference/getc-getwc.md), [ GetChar](../c-runtime-library/reference/getc-getwc.md), [získá](../c-runtime-library/gets-getws.md), [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), a [ungetc –](../c-runtime-library/reference/ungetc-ungetwc.md)  
  
-   Funkce zápisu bajtů – [fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputc –](../c-runtime-library/reference/fputc-fputwc.md), [fputs –](../c-runtime-library/reference/fputs-fputws.md), [fwrite –](../c-runtime-library/reference/fwrite.md), [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [putc –](../c-runtime-library/reference/putc-putwc.md), [putchar –](../c-runtime-library/reference/putc-putwc.md), [vloží](../c-runtime-library/reference/puts-putws.md), [vfprintf –](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), a [vprintf –](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)  
  
-   Funkce pozice – [fflush –](../c-runtime-library/reference/fflush.md), [fseek](../c-runtime-library/reference/fseek-fseeki64.md), [fsetpos –](../c-runtime-library/reference/fsetpos.md), a [rewind](../c-runtime-library/reference/rewind.md)  
  
 Funkce v zbývající dvě skupiny, které jsou deklarované v \<wchar.h >:  
  
-   Rámci celé načíst funkce – [fgetwc –](../c-runtime-library/reference/fgetc-fgetwc.md), [fgetws –](../c-runtime-library/reference/fgets-fgetws.md), [fwscanf –](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getwc –](../c-runtime-library/reference/getc-getwc.md), [getwchar –](../c-runtime-library/reference/getc-getwc.md), [ungetwc –](../c-runtime-library/reference/ungetc-ungetwc.md), a [wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),  
  
-   Zápis rámci celé funkce – [fwprintf –](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputwc –](../c-runtime-library/reference/fputc-fputwc.md), [fputws –](../c-runtime-library/reference/fputs-fputws.md), [putwc –](../c-runtime-library/reference/putc-putwc.md), [putwchar –](../c-runtime-library/reference/fputc-fputwc.md), [vfwprintf –](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vwprintf –](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), a [wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),  
  
 Stav diagram znázorňuje, musí volat jedna z funkcí pozici mezi většinu operací čtení a zápisu:  
  
-   Čtení funkci nelze volat, pokud byla poslední operace v datovém proudu pro zápis.  
  
-   Funkce zápisu nelze volat byla-li poslední operace v datovém proudu pro čtení, pokud, přečtěte si, že operace nastaven indikátoru end souborového.  
  
 Nakonec stavu diagram znázorňuje, pozice operace nikdy snižuje počet volání platnou funkcí, které můžete provést.  
  
## <a name="see-also"></a>Viz také  
 [Soubory a proudy](../c-runtime-library/files-and-streams.md)