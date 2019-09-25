---
title: Upozornění kompilátoru C4577
description: Upozornění kompilátoru C4577 popis a řešení.
ms.date: 09/18/2019
helpviewer_keywords:
- C4577
ms.openlocfilehash: 637023f4c27f93238fbbd13b4a0e652e6cd958e0
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71241099"
---
# <a name="compiler-warning-level-1-c4577"></a>Upozornění kompilátoru (úroveň 1) C4577

> ' s výjimkou ' se používá bez zadaného režimu zpracování výjimek; ukončení u výjimky není zaručeno. Zadat/EHsc

Kompilátor zjistil `noexcept` specifikaci, ale nebylo zadáno standardní C++ zpracování výjimky. Kompilátor plně nepodporuje zpracování výjimek v C++ závislosti na standardu, pokud není zadána možnost kompilátoru [/EHsc](../../build/reference/eh-exception-handling-model.md) . Chcete-li tento problém vyřešit, nastavte možnost kompilátoru **/EHsc** .

Toto upozornění je v aplikaci Visual Studio 2015 novinkou a je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
