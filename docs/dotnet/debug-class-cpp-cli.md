---
title: "Debug – třída (C + +/ CLI) | Microsoft Docs"
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
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 236a40873d3cbd660f9999880d46df4f91632b2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="debug-class-ccli"></a>Debug – třída (C++/CLI)
Při použití <xref:System.Diagnostics.Debug> v aplikaci Visual C++, nezmění chování mezi ladění a sestavení pro vydání.  
  
## <a name="remarks"></a>Poznámky  
 Chování <xref:System.Diagnostics.Trace> je stejný jako u chování pro třídu ladění, ale závisí na symbol trasování definovaný. To znamená, že musíte `#ifdef` jakýkoli související trasování kód, abyste zabránili ladění chování v sestavení pro vydání.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující ukázka vždy provede výstupní příkazy, bez ohledu na to, jestli je kompilovat s **/DDEBUG** nebo **/DTRACE**.  
  
### <a name="code"></a>Kód  
  
```  
// mcpp_debug_class.cpp  
// compile with: /clr  
#using <system.dll>  
using namespace System::Diagnostics;  
using namespace System;  
  
int main() {  
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );  
   Trace::AutoFlush = true;  
   Trace::Indent();  
   Trace::WriteLine( "Entering Main" );  
   Console::WriteLine( "Hello World." );  
   Trace::WriteLine( "Exiting Main" );  
   Trace::Unindent();  
  
   Debug::WriteLine("test");  
}  
```  
  
### <a name="output"></a>Výstup  
  
```  
    Entering Main  
Hello World.  
    Exiting Main  
test  
```  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Chcete-li získat očekávané chování (tj. žádný výstup "test" vytisknout pro sestavení pro vydání aplikace), je nutné použít `#ifdef` a `#endif` direktivy. V předchozím příkladu kódu je změněna, k předvedení tuto opravu:  
  
### <a name="code"></a>Kód  
  
```  
// mcpp_debug_class2.cpp  
// compile with: /clr  
#using <system.dll>  
using namespace System::Diagnostics;  
using namespace System;  
  
int main() {  
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );  
   Trace::AutoFlush = true;  
   Trace::Indent();  
  
#ifdef TRACE   // checks for a debug build  
   Trace::WriteLine( "Entering Main" );  
   Console::WriteLine( "Hello World." );  
   Trace::WriteLine( "Exiting Main" );  
#endif  
   Trace::Unindent();  
  
#ifdef DEBUG   // checks for a debug build  
   Debug::WriteLine("test");  
#endif   //ends the conditional block  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)