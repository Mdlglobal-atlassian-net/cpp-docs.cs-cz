---
title: "Obecné jazykové změny (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 87ff7f55b67c4e8a84d15099432962ee0939d13a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="general-language-changes-ccli"></a>Obecné jazykové změny (C++/CLI)
Počet funkce modulu CLR jazyka změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Změn popsaných v této části jsou řazení směsicí jazyka. Obsahuje změnu při manipulaci s textové literály, změnu rozlišení přetížení mezi třemi tečkami a `Param` atribut, změna `typeof` k `typeid`, změnu volání konstruktoru inicializátoru seznamů a Úvod nový zápis přetypování u `safe_cast`.  
  
 [Řetězcový literál](../dotnet/string-literal.md)  
 Popisuje, jak se změnila zpracování literálů řetězce.  
  
 [Pole parametrů a tři tečky](../dotnet/param-array-and-ellipsis.md)  
 Popisuje, jak `ParamArray` nyní je dána přednost se třemi tečkami (`...`) pro rozlišování funkce volání s proměnlivým počtem argumentů.  
  
 [typeof přechází na T::typeid](../dotnet/typeof-goes-to-t-typeid.md)  
 Popisuje, jak `typeof` byl nahrazen operátor `typeid`.  
  
 [Seznamy inicializátorů](../dotnet/initializer-lists.md)  
 Popisuje změny v pořadí volání inicializační seznamy.  
  
 [Zápis přetypování a úvod do operace safe_cast<>](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)  
 Popisuje změny na zápis přetypování a zejména zavedení `safe_cast`.  
  
## <a name="see-also"></a>Viz také  
 [Základy migrace v jazyce C++/CLI](../dotnet/cpp-cli-migration-primer.md)