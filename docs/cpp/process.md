---
title: zpracování
ms.date: 11/04/2016
f1_keywords:
- process_cpp
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
ms.openlocfilehash: 049360dddff2b9ca2ea460b96e027e86899f1ecb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344999"
---
# <a name="process"></a>zpracování

Určuje, že proces spravované aplikace by měl používat jednu kopii určité globální proměnné, statické členské proměnné nebo statické místní proměnné sdílené ve všech doménách aplikace v procesu. To byla primárně určena pro použití při kompilaci s **/CLR: pure**, které jsou zastaralé v sadě Visual Studio 2017 a v sadě Visual Studio 2017 není podporován. Při kompilaci s **/CLR**, globální a statické proměnné na úrovni jednotlivého procesu ve výchozím nastavení a není nutné používat **__declspec(process)**.

Může být označena pouze globální proměnné, statické členské proměnné nebo statické místní proměnná nativního typu **__declspec(process)**.

**proces** je platná jenom při kompilaci s [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

Pokud chcete, aby každá doména aplikace měla vlastní kopii globální proměnné, použijte [appdomain](../cpp/appdomain.md).

Zobrazit [aplikačních doménách a Visual C++](../dotnet/application-domains-and-visual-cpp.md) Další informace.

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
