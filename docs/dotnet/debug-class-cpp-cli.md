---
title: Debug – třída (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
ms.openlocfilehash: ae400783112ca44a75f1224a9e8d6ebe52414070
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662472"
---
# <a name="debug-class-ccli"></a>Debug – třída (C++/CLI)

Při použití <xref:System.Diagnostics.Debug> v aplikaci Visual C++, nezmění chování mezi ladění a sestavení pro vydání.

## <a name="remarks"></a>Poznámky

Chování <xref:System.Diagnostics.Trace> je stejný jako chování pro třídu ladění, ale závisí na symbol trasování je definována. To znamená, že musíte `#ifdef` žádný trasování související kód, zabránit chování při ladění v sestavení pro vydání.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad provede vždy výstupní příkazy, bez ohledu na to, ať už kompilujete s **/DDEBUG** nebo **/DTRACE**.

### <a name="code"></a>Kód

```cpp
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

```Output
    Entering Main
Hello World.
    Exiting Main
test
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Chcete-li získat očekávané chování (tj. žádný výstup "test" tisk pro sestavení pro vydání aplikace), je nutné použít `#ifdef` a `#endif` direktivy. Předchozí ukázce kódu je předvést tato oprava změny níže:

### <a name="code"></a>Kód

```cpp
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