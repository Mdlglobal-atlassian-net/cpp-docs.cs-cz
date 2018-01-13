---
title: Kompatibilita | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.programs
dev_langs: C++
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f14d330ada8f71cc3556b7151189968b43cff4ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compatibility"></a>Kompatibilita
Univerzální knihoven C Run-Time (UCRT) podporuje většinu standardní knihovny jazyka C požadované pro přizpůsobení C++. Implementuje knihovnu C99 (ISO/IEC 9899:1999) s výjimky obecného typu makra definované v \<tgmath.h > a striktní typ kompatibility v \<complex.h >. UCRT také implementuje podmnožinu POSIX.1 velké (ISO/IEC 9945-1:1996, rozhraní API systému POSIX) knihovny jazyka C, ale není plně vyhovující pro všechny konkrétní standard POSIX.  Kromě toho UCRT implementuje několik specifické pro společnost Microsoft funkcemi a makry, které nejsou součástí standardní.  
  
 Funkce, které jsou specifické pro implementaci společnosti Microsoft Visual C++ se nacházejí v knihovně vcruntime.  Mnoho z těchto funkcí jsou pro interní použití a nedají se volat pomocí uživatelského kódu. Některé jsou popsány pro použití v ladění a implementace kompatibility.  
  
 Standardní C++ si vyhrazuje názvy, které začínají podtržítkem v globálním oboru názvů pro implementaci. Protože POSIX funkce jsou v globálním oboru názvů, ale nejsou součástí standardní běhové knihovny jazyka C, implementace specifické pro společnost Microsoft tyto funkce mají úvodní podtržítka. Pro přenositelnost UCRT podporuje také výchozí názvy, ale Visual C++ compiler vystaví vyřazení upozornění, když kompilace kódu, který používá je. Na výchozí POSIX názvy jsou zastaralé, není funkce. Chcete-li potlačit upozornění, definovat `_CRT_NONSTDC_NO_WARNINGS` před zahrnutím všechny hlavičky v kódu, který používá původní názvy POSIX.  
  
 Určité funkce standardní knihovny jazyka C mít historii unsafe využití z důvodu chybná parametry a zaškrtnuté políčko vyrovnávací paměti. Tyto funkce jsou často zdroj problémy se zabezpečením v kódu. Společnost Microsoft vytvořila sadu bezpečnější verze těchto funkcí, které ověřte použití parametrů a má neplatný parametr obslužná rutina volat, když se zjistí problém v době běhu.  Ve výchozím nastavení Visual C++ compiler vydá upozornění vyřazení při použití funkce, který má k dispozici bezpečnější variantu. Při kompilaci kódu jako C++, můžete definovat `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1 eliminovat většinu upozornění. K volání bezpečnější variant při zachování přenosné zdrojového kódu používá přetížení šablony. Chcete-li potlačit upozornění, definovat `_CRT_SECURE_NO_WARNINGS` před zahrnutím všechny hlavičky v kódu, který používá tyto funkce. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md).  
  
 S výjimkou toho, jak je uvedeno v dokumentaci pro konkrétní funkce, je kompatibilní s rozhraním API systému Windows UCRT.  Některé funkce nejsou podporovány v aplikacích pro Windows 8 Store nebo univerzální aplikace pro Windows ve Windows 10. Tyto funkce jsou uvedeny v [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx), který vytvoří výčet funkcí, které nepodporují [prostředí Windows Runtime](http://msdn.microsoft.com/en-us/9a1a18b8-9802-4ec5-b9de-0d2dfdf414e9).  
  
## <a name="related-articles"></a>Související články  
  
|Název|Popis|  
|-----------|-----------------|  
|[Aplikace pro Windows Store, prostředí Windows Runtime a knihovna CRT](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|Popisuje, pokud rutiny UCRT nejsou kompatibilní s univerzální aplikace pro Windows nebo aplikace pro Windows Store.|  
|[Kompatibilita s ANSI C](../c-runtime-library/ansi-c-compliance.md)|Popisuje kompatibilní se standardem standardní pojmenování v UCRT.|  
|[UNIX](../c-runtime-library/unix.md)|Poskytuje pokyny pro přenos programů UNIX.|  
|[Platformy systému Windows (CRT)](../c-runtime-library/windows-platforms-crt.md)|Seznam operačních systémů, které jsou CRT podporuje.|  
|[Zpětná kompatibilita](../c-runtime-library/backward-compatibility.md)|Popisuje, jak mapování názvů staré CRT k nové.|  
|[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)|Obsahuje přehled možností přidružené kompilátoru a soubory CRT knihovny (LIB).|