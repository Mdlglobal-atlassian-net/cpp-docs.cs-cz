---
title: Domény aplikace a jazyk Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
ms.openlocfilehash: 2296654e6935bc40f301226b184cf34f77cb126d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539266"
---
# <a name="application-domains-and-visual-c"></a>Aplikační domény a Visual C++

Pokud máte `__clrcall` virtuální funkce, tabulku vtable budou podle domény aplikace (appdomain). Pokud vytvoříte objekt v jedné doméně appdomain, lze volat pouze virtuální funkci z této domény. Ve smíšeném režimu (**/CLR**) bude mít na úrovni jednotlivého procesu vtable, pokud typ nemá žádné `__clrcall` virtuální funkce. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Další informace naleznete v tématu:

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [process](../cpp/process.md)

## <a name="see-also"></a>Viz také:

- [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)