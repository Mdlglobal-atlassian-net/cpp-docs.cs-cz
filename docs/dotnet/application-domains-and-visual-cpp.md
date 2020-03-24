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
ms.openlocfilehash: 16c02bb58681ecb241d3552f57e0b05f2d6711b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208796"
---
# <a name="application-domains-and-visual-c"></a>Domény aplikace a jazyk Visual C++

Pokud máte virtuální funkci `__clrcall`, tabulka vtable bude vázaná na doménu aplikace (AppDomain). Vytvoříte-li objekt v jedné doméně aplikace, můžete volat pouze virtuální funkce v rámci této domény AppDomain. Ve smíšeném režimu ( **/CLR**) budete mít k dispozici vtable pro procesy, pokud váš typ nemá žádné `__clrcall` virtuální funkce. Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

Další informace naleznete v tématu:

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [process](../cpp/process.md)

## <a name="see-also"></a>Viz také

- [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)
