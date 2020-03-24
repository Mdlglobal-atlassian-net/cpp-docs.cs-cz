---
title: Upozornění kompilátoru (úroveň 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: c39848b9b3e94e35c4d0c0937a0974b717c6bd8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198173"
---
# <a name="compiler-warning-level-4-c4710"></a>Upozornění kompilátoru (úroveň 4) C4710

' function ': funkce není vložena

Daná funkce byla vybrána pro vložené rozšíření, ale kompilátor neprováděl vkládání.

Vkládání je prováděno podle uvážení kompilátoru. Klíčové slovo **inline** , podobně jako klíčové slovo **Register** , je použito jako pomocný parametr pro kompilátor. Kompilátor používá heuristicky k určení, zda by měl vložit konkrétní funkci pro zrychlení kódu při kompilování pro rychlost, nebo pokud by měla být vložena určitá funkce, aby byl kód při kompilování pro prostor menší. Kompilátor bude při kompilaci pro místo vložen pouze velmi malými funkcemi.

V některých případech kompilátor nevloží určitou funkci z mechanických důvodů. Seznam důvodů, které kompilátor nemusí vložit do funkce, najdete v tématu [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) .

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .
