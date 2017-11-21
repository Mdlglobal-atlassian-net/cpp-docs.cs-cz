---
title: "Postupy: určení, zda bylo zahájeno vypínání (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
ms.assetid: a8d39731-dea8-4f0a-96b7-2a5de09b21d7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7f4575f212752a43df2b130fbde9aa7264186d6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-determine-if-shutdown-has-started-ccli"></a>Postupy: Zjištění, zda bylo zahájeno vypínání (C++/CLI)
Následující příklad kódu ukazuje, jak zjistit, zda je aktuálně ukončení aplikace nebo rozhraní .NET Framework. To je užitečné pro přístup k statických elementů v rozhraní .NET Framework, protože během vypnutí, tyto konstrukce, jsou dokončeny systémem a nelze jej použít spolehlivě. Kontrolou <xref:System.Environment.HasShutdownStarted%2A> vlastnost nejprve můžete vyhnout potenciální selhání přístupu k těmto prvkům.  
  
## <a name="example"></a>Příklad  
  
```  
// check_shutdown.cpp  
// compile with: /clr  
using namespace System;  
int main()   
{  
   if (Environment::HasShutdownStarted)  
      Console::WriteLine("Shutting down.");  
   else  
      Console::WriteLine("Not shutting down.");  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Operace systému Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)