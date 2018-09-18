---
title: proces | Dokumentace Microsoftu
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
ms.openlocfilehash: 65ae8eef828a8abd4bf726c99850089c0f30b71b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032561"
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
