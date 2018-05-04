---
title: Omezení kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc7cd26add0a46bab8df7669fb6dfb6060b0010e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="compiler-limits"></a>Omezení kompilátoru
Standard jazyka C++ doporučuje limity pro různé jazykové konstrukce. Následuje seznam případů, kdy Visual C++ compiler neimplementuje doporučené omezení. První číslo je limit, který je vytvořen v ISO C++ 11 standardní (INCITS nebo ISO/IEC 14882-2011 [2012] přílohy B) a druhé číslo, které je implementováno modulem Visual C++ omezení:  
  
-   Složené příkazy, iterace řídicí struktury a výběr úrovně vnoření řízení struktury - C++ standardní: 256, – kompilátor Visual C++: závisí na kombinaci příkazů, které jsou vnořené, ale obecně rozsahu od 100 do 110.  
  
-   Parametry v definici jeden makro - C++ standardní: 256, – kompilátor Visual C++: 127 znaků.  
  
-   Argumenty v jedné makro volání - standardní C++: 256, kompilátor Visual C++ 127 znaků.  
  
-   Řetězec znaků znak literálu nebo široké řetězcový literál (po zřetězení) – C++ standard: 65536, – kompilátor Visual C++: 65535 jednobajtové znaky, včetně `null` ukončovací a 32767 dvoubajtové znaky, včetně `null` ukončovací znak.  
  
-   Úrovně vnořené třídy, struktury a sjednocení definice v jediném `struct-declaration-list` -C++ standard: 256, – kompilátor Visual C++: 16.  
  
-   Inicializátory člen v definici konstruktor - C++ standardní: 6144, – kompilátor Visual C++: minimálně 6144.  
  
-   Obor kvalifikaci jeden identifikátor - C++ standardní: 256, – kompilátor Visual C++: 127 znaků.  
  
-   Vnořené `extern` specifikace - C++ standardní: 1024 – kompilátor Visual C++: 9 (není počítání implicitní `extern` specifikace v globálním oboru nebo 10, pokud je počet implicitní `extern` specifikace v globálním oboru...  
  
-   Argumenty šablony v deklaraci šablony - C++ standardní: 1024 – kompilátor Visual C++: 2046.  
  
## <a name="see-also"></a>Viz také  
 [Nestandardní chování](../cpp/nonstandard-behavior.md)