---
title: proces | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- process_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b36ec42447aa076d0623707951f82b7b9c95d563
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704903"
---
# <a name="process"></a>zpracování

Určuje, že proces spravované aplikace by měl používat jednu kopii určité globální proměnné, statické členské proměnné nebo statické místní proměnné sdílené ve všech doménách aplikace v procesu. To se primárně určen pro použití při kompilaci s **/CLR: pure**, který je ve Visual Studio 2017 zastaralá a není podporována v Visual Studio 2017. Při kompilaci s **/CLR**, jsou statické a globální proměnné na proces ve výchozím nastavení a nemusíte používat `__declspec(process)`.

Modifikátorem `__declspec(process)` může být označena pouze globální, statická členská nebo statická místní proměnná nativního typu.

`process` je platný pouze při kompilaci s [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

Pokud chcete domén aplikace, které chcete mít svůj vlastní kopii globální proměnné, použijte [appdomain](../cpp/appdomain.md).

V tématu [domény aplikace a jazyk Visual C++](../dotnet/application-domains-and-visual-cpp.md) Další informace.

## <a name="see-also"></a>Viz také:

- [__declspec](../cpp/declspec.md)
- [Klíčová slova](../cpp/keywords-cpp.md)
