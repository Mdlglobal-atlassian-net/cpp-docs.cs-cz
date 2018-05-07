---
title: Obecné jazykové změny (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: aede6cc0d4bd8e50d8662f301ffdfb7b6179a230
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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