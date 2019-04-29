---
title: Kompilátor upozornění (úroveň 1) C4655
ms.date: 08/27/2018
f1_keywords:
- C4655
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
ms.openlocfilehash: aff78dbed217a6d9c5bc2a315ef12a33fe6caf0d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374661"
---
# <a name="compiler-warning-level-1-c4655"></a>Kompilátor upozornění (úroveň 1) C4655

> "*symbol*': typ proměnné je nový od posledního sestavení, nebo je někde definovaný nějak jinak

## <a name="remarks"></a>Poznámky

Změnit nebo přidat nový typ dat od posledního úspěšného sestavení. Upravit a pokračovat nepodporuje změny na stávající datové typy.

Toto upozornění je následována [závažná chyba C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Další informace najdete v tématu [podporované změny kódu](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Chcete-li odebrat toto upozornění bez ukončení aktuální relace ladění

1. Změna datového typu zpět do stavu před chybou.

2. Z **ladění** nabídce zvolte **použít změny kódu**.

### <a name="to-remove-this-warning-without-changing-your-source-code"></a>Chcete-li odebrat toto upozornění bez změny zdrojového kódu

1. Z **ladění** nabídce zvolte **Zastavit ladění**.

2. Z **sestavení** nabídce zvolte **sestavení**.