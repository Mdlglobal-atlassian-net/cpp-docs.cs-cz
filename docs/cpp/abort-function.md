---
title: abort – funkce
ms.date: 12/01/2017
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
ms.openlocfilehash: 7c87cb4fe7349a0d623c765c20e7e213a8454571
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451230"
---
# <a name="abort-function"></a>abort – funkce

**Přerušit** deklarovaná také ve standardním vloženém souboru \<stdlib.h >, ukončuje program jazyka C++. Rozdíl mezi `exit` a **přerušit** je, že `exit` umožňuje zpracování ukončení za běhu jazyka C++ uskutečnit (globální objekt zavolány destruktory), zatímco **přerušit** Ukončí program okamžitě. Další informace najdete v tématu [přerušit](../c-runtime-library/reference/abort.md) v *Run-Time Library Reference*.

## <a name="see-also"></a>Viz také:

[Ukončení programu](../cpp/program-termination.md)