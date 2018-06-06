---
title: Aplikační domény a Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b935b9a5d1561fa1c8b961ee48b92f59b98e2bd2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704331"
---
# <a name="application-domains-and-visual-c"></a>Aplikační domény a Visual C++

Pokud máte `__clrcall` virtuální funkce tabulce vtable bude podle domény aplikace (appdomain). Pokud vytvoříte objekt v jedné doméně aplikace, může volat pouze virtuální funkci z této domény. Ve smíšeném režimu (**/CLR**) bude mít na proces virtuálních tabulek, pokud váš typ nemá žádné `__clrcall` virtuální funkce. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Další informace naleznete v tématu:

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [process](../cpp/process.md)

## <a name="see-also"></a>Viz také:

- [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)