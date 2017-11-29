---
title: "Postupy: načtení doby uplynulé od spuštění (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
ms.assetid: a31fdecc-099e-4dd1-a176-f682289c5dd0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 56f73aec78af0fe34d8c3881911a6ae1d7f26501
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-retrieve-time-elapsed-since-startup-ccli"></a>Postupy: Načtení doby uplynulé od spuštění (C++/CLI)
Následující příklad kódu ukazuje, jak určit počet značek, nebo počet milisekund, které uplynuly od systému Windows byla spuštěna. Tato hodnota je uložena v <xref:System.Environment.TickCount%2A?displayProperty=fullName> člen a, protože je hodnotu 32-bit, obnoví na nulu přibližně každých 24.9 dnů.  
  
## <a name="example"></a>Příklad  
  
```  
// startup_time.cpp  
// compile with: /clr  
using namespace System;  
  
int main( )   
{  
   Int32 tc = Environment::TickCount;  
   Int32 seconds = tc / 1000;  
   Int32 minutes = seconds / 60;  
   float hours = static_cast<float>(minutes) / 60;  
   float days = hours / 24;  
  
   Console::WriteLine("Milliseconds since startup: {0}", tc);  
   Console::WriteLine("Seconds since startup: {0}", seconds);  
   Console::WriteLine("Minutes since startup: {0}", minutes);  
   Console::WriteLine("Hours since startup: {0}", hours);  
   Console::WriteLine("Days since startup: {0}", days);  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Operace systému Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)