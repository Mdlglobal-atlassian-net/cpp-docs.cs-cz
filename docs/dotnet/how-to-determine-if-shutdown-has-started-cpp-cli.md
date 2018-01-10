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
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4d89fa475c997e0842ef9de5a21c26e664f25d78
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)