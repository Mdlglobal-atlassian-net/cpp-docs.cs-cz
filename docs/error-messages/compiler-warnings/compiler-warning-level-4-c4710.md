---
title: Upozornění (úroveň 4) C4710 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4710
dev_langs:
- C++
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f6de17f7005db3834bfcfc93aff03f12f0293ce
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046092"
---
# <a name="compiler-warning-level-4-c4710"></a>Kompilátor upozornění (úroveň 4) C4710

'function': funkce není vložena

Dané funkce byla vybrána pro vložené rozšíření, ale kompilátor neprovedli vkládání.

Vkládání se provádí na základě vlastního uvážení kompilátoru. **Vložené** – klíčové slovo, třeba **zaregistrovat** – klíčové slovo, se používají jako Nápověda pro kompilátor. Kompilátor používá heuristiku k určení, pokud by měl vložení funkce pro urychlení kódu při kompilaci pro rychlost, nebo pokud by měl vložení funkce zmenšit kód při kompilaci pro prostor. Kompilátor bude pouze vložené při kompilaci pro prostor velmi malé funkce.

V některých případech kompilátor nevloží určitou funkci mechanických důvodů. Zobrazit [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) seznam důvodů kompilátor může funkce.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.