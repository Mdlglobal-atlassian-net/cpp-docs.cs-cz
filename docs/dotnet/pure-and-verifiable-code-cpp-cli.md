---
title: Čistý a ověřitelný kód (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 453bb40e94c1d345adbe22f8792b59d1e584499a
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704825"
---
# <a name="pure-and-verifiable-code-ccli"></a>Čistý a ověřitelný kód (C + +/ CLI)

Visual C++ v aplikaci Visual Studio 2017 programování rozhraní .NET podporuje vytváření smíšená sestavení pomocí [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru. **/CLR: pure** a **CLR: safe** možnosti jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017. Pokud váš kód musí být bezpečné nebo ověřitelný, pak doporučujeme portu jazyka C#.

## <a name="mixed-clr"></a>Smíšená (/ clr)

Smíšená sestavení (Kompilovat s **/CLR**), obsahuje obě nespravované a spravované části, což jim umožňuje používat funkce rozhraní .NET, ale stále obsahuje nativního kódu. To umožňuje aplikací a součástí aktualizovat bez nutnosti, že se celý projekt přepsaná použití funkcí rozhraní .NET. Pomocí Visual C++ kombinovat spravovaná a nativní kód tímto způsobem se nazývá zprostředkovatele komunikace C++. Další informace najdete v tématu [Mixed (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md) a [nativní a interoperabilitě .NET](../dotnet/native-and-dotnet-interoperability.md).

Volání ze spravovaných sestavení do nativních knihoven DLL prostřednictvím P/Invoke bude kompilovat, ale může dojít k selhání za běhu v závislosti na nastavení zabezpečení.

Existuje jedna situace kódování, která bude úspěšně zkompilována, ale povede k neověřitelnému sestavení: volání virtuální funkce instancí objektu pomocí operátoru pro rozlišení oboru.  Příklad: `MyObj -> A::VirtualFunction();`.

## <a name="see-also"></a>Viz také:

- [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

