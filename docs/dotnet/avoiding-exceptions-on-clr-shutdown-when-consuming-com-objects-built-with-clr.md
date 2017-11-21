---
title: "Zamezení výjimky vyvolané objektů COM sestavených s - clr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 430420a62915d3378dae863c20c00e3b398ecb3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Obcházení výjimek na vypnutí CLR při spotřebě objektů COM sestavených s volbou /clr
Jakmile modul CLR (CLR) přejde do režimu vypnutí, nativní funkce mají omezený přístup ke službám CLR. Při pokusu o volání verze v objektu COM kompilovat s **/CLR**, modul CLR přechází do nativního kódu a potom přejde zpět do spravovaného kódu pro volání IUnknown::Release (která je definovaná ve spravovaném kódu). Modulu CLR zabraňuje volání zpět do spravovaného kódu, protože je v režimu vypnutí.  
  
 To vyřešit, zkontrolujte, destruktory volat z verze metody obsahovat pouze nativní kód.  
  
## <a name="see-also"></a>Viz také  
 [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)