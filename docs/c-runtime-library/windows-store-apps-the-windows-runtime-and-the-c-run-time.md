---
title: "Aplikace pro Windows Store, prostředí Windows Runtime a C Run-Time | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b332e392db2ca788d041cb73e73cf42cce85906c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="windows-store-apps-the-windows-runtime-and-the-c-run-time"></a>Aplikace pro web Windows Store, prostředí Windows Runtime a knihovna CRT
[!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]aplikace jsou programy, které běží v prostředí Windows Runtime, který je prováděn [!INCLUDE[win8](../build/reference/includes/win8_md.md)].  Prostředí Windows Runtime je důvěryhodného prostředí, které řídí funkce, proměnné a prostředky, které jsou k dispozici [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikace. Ale standardně omezení prostředí Windows Runtime zabránit používání většinu funkcí běhové knihovny jazyka C (CRT) v [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikace.  
  
 Prostředí Windows Runtime nepodporuje následující funkce CRT:  
  
-   Většina funkcí CRT, které se vztahují k nepodporované funkce.  
  
     Například [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikace nelze vytvořit proces pomocí `exec` a `spawn` rodiny rutiny.  
  
     Když CRT funkce není podporována. v [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikace, že je skutečnost uvedena v článku o jeho.  
  
-   Většina vícebajtové znaky a řetězce funkce.  
  
     Kódování Unicode a ANSI text jsou však podporovány.  
  
-   Aplikace konzoly a argumenty příkazového řádku.  
  
     Tradiční aplikace klasické pracovní plochy však stále podporují konzoly a argumenty příkazového řádku.  
  
-   Proměnné prostředí.  
  
-   Koncept aktuální pracovní adresář.  
  
-   [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]aplikace a knihovny DLL, které jsou staticky propojené s CRT a sestaveny pomocí tohoto [/MT](../build/reference/md-mt-ld-use-run-time-library.md) nebo `/MTd` – možnosti kompilátoru.  
  
     To znamená, aplikaci, která používá s více vlákny, statické verzi CRT.  
  
-   Aplikace vytvořené pomocí [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) – možnost kompilátoru.  
  
     To znamená, ladění, vícevláknový a verze specifické DLL Knihovny CRT. Tato aplikace nepodporuje [!INCLUDE[win8_appstore_long](../build/reference/includes/win8_appstore_long_md.md)].  
  
 Úplný seznam funkcí CRT, které nejsou k dispozici v [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikace a návrhy pro alternativní funkce, najdete v části [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="see-also"></a>Viz také  
 [Kompatibilita](../c-runtime-library/compatibility.md)   
 [Nepodporované funkce CRT prostředí Windows Runtime](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)   
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)