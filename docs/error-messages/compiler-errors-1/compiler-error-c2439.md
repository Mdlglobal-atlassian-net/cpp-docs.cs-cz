---
title: Chyba kompilátoru C2439 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2439
dev_langs:
- C++
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 419bf7be45a1383135d0231cd059837e1fe62729
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058409"
---
# <a name="compiler-error-c2439"></a>Chyba kompilátoru C2439

'identifier': člen nešel inicializovat

Třídy, struktury nebo člen sjednocení nelze inicializovat.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Došlo k pokusu o inicializaci nepřímá základní třída nebo struktura.

1. Došlo k pokusu o inicializaci zděděného člena třídy nebo struktury. Zděděný člen musí být inicializován pomocí konstruktoru třídy nebo struktury.