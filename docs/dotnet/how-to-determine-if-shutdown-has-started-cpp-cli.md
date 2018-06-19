---
title: 'Postupy: určení, zda bylo zahájeno vypínání (C + +/ CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
ms.assetid: a8d39731-dea8-4f0a-96b7-2a5de09b21d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bbcc2b1efa54808b25238bde4de3dcc21d2ba687
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137699"
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