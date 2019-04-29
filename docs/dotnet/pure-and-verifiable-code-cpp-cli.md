---
title: Čistý a ověřitelný kód (C++/CLI)
ms.date: 11/04/2016
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
ms.openlocfilehash: 66f3b5a33791d20297cde6e6223ba65189a99682
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384711"
---
# <a name="pure-and-verifiable-code-ccli"></a>Čistý a ověřitelný kód (C++vyhodnocovací)

Pro programování v rozhraní .NET, Visual C++ v sadě Visual Studio 2017 podporuje vytváření smíšená sestavení s použitím [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru. **/CLR: pure** a **CLR: safe** možnosti jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017. Pokud váš kód musí být bezpečné nebo ověřit, pak doporučujeme port na C#.

## <a name="mixed-clr"></a>Smíšená (/ clr)

Smíšená sestavení (zkompilovaná **/CLR**), obsahuje obě nespravované a spravované části, což jim umožňuje používat funkce rozhraní .NET, ale stále obsahuje nativní kód. Díky tomu aplikace a komponenty aktualizovat, pokud chcete používat funkce .NET bez nutnosti, být přepsán celý projekt. Pomocí Visual C++ pro kombinaci spravovaného a nativního kódu tímto způsobem se nazývá zprostředkovatele komunikace C++. Další informace najdete v tématu [smíšený (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md) a [nativní a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md).

Volání ze spravovaných sestavení nativních knihoven DLL prostřednictvím P/Invoke zkompiluje, ale může dojít k selhání za běhu v závislosti na nastavení zabezpečení.

Existuje jedna situace kódování, která bude úspěšně zkompilována, ale povede k neověřitelnému sestavení: volání virtuální funkce instancí objektu pomocí operátoru pro rozlišení oboru.  Například: `MyObj -> A::VirtualFunction();`.

## <a name="see-also"></a>Viz také:

- [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
