---
title: Upozornění kompilátoru C4577
description: Upozornění kompilátoru C4577 popis a řešení.
ms.date: 09/18/2019
f1_keywords:
- C4577
helpviewer_keywords:
- C4577
ms.openlocfilehash: e29e47b2a268d86f7f6a280b79a1604fe6eff8a4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810567"
---
# <a name="compiler-warning-level-1-c4577"></a>Upozornění kompilátoru (úroveň 1) C4577

> ' s výjimkou ' se používá bez zadaného režimu zpracování výjimek; ukončení u výjimky není zaručeno. Zadat/EHsc

Kompilátor zjistil specifikaci `noexcept`, ale nebylo zadáno standardní C++ zpracování výjimek. Kompilátor plně nepodporuje zpracování výjimek v C++ závislosti na standardu, pokud není zadána možnost kompilátoru [/EHsc](../../build/reference/eh-exception-handling-model.md) . Chcete-li tento problém vyřešit, nastavte možnost kompilátoru **/EHsc** .

Toto upozornění je v aplikaci Visual Studio 2015 novinkou a je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
