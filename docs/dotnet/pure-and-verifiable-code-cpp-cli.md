---
title: "Čistý a ověřitelný kód (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], verifiable assemblies
- /clr compiler option [C++], mixed assemblies
- pure MSIL [C++]
- verifiable assemblies [C++]
- verifiably type-safe code [C++]
- /clr compiler option [C++], pure assemblies
- .NET Framework [C++], pure and verifiable code
- assemblies [C++], mixed code
- verifiable assemblies [C++], about verifiable assemblies
- mixed assemblies [C++], about mixed assemblies
- pure MSIL [C++], about pure code
- assemblies [C++], verifiable code
- mixed assemblies [C++]
- assemblies [C++], pure code
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9ba218772bdedf772e995bb9289b18452d599e6c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="pure-and-verifiable-code-ccli"></a>Čistý a ověřitelný kód (C++/CLI)
Visual C++ v aplikaci Visual Studio 2017 programování rozhraní .NET podporuje vytváření smíšená sestavení pomocí [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru. **/CLR: pure** a **CLR: safe** možnosti jsou zastaralé od verze sady Visual Studio 2015 a bude v budoucí verzi systému kompilátoru odebrána. Pokud musí být ověřitelný kód, pak doporučujeme portu jazyka C#.
  
## <a name="mixed-clr"></a>Smíšená (/ clr)  
 Smíšená sestavení (Kompilovat s **/CLR**), obsahuje obě nespravované a spravované části, což jim umožňuje používat funkce rozhraní .NET, ale stále obsahuje nativního kódu. To umožňuje aplikací a součástí aktualizovat bez nutnosti, že se celý projekt přepsaná použití funkcí rozhraní .NET. Pomocí Visual C++ kombinovat spravovaná a nativní kód tímto způsobem se nazývá zprostředkovatele komunikace C++. Další informace najdete v tématu [Mixed (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md) a [nativní a interoperabilitě .NET](../dotnet/native-and-dotnet-interoperability.md).  
  
  
Volání ze spravovaných sestavení do nativních knihoven DLL prostřednictvím P/Invoke bude kompilovat, ale může dojít k selhání za běhu v závislosti na nastavení zabezpečení.  
  
Existuje jedna situace kódování, která bude úspěšně zkompilována, ale povede k neověřitelnému sestavení: volání virtuální funkce instancí objektu pomocí operátoru pro rozlišení oboru.  Příklad: `MyObj -> A::VirtualFunction();`.  
  
## <a name="see-also"></a>Viz také  
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
