---
title: Debug – třída (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
ms.openlocfilehash: 3a262a0d2ef429cb94f4648eb7c7180e7b130279
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393776"
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

## <a name="see-also"></a>Viz také:

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
