---
title: "Omezení kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e64bedc169fb4737a7e16175099df5571df82ef2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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