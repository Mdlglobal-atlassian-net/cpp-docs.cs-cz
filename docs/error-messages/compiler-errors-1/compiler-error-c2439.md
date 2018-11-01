---
title: Chyba kompilátoru C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: f71112d3f37f3e4d1a4f41bade95726d7aa0a0bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644353"
---
# <a name="compiler-error-c2439"></a>Chyba kompilátoru C2439

'identifier': člen nešel inicializovat

Třídy, struktury nebo člen sjednocení nelze inicializovat.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Došlo k pokusu o inicializaci nepřímá základní třída nebo struktura.

1. Došlo k pokusu o inicializaci zděděného člena třídy nebo struktury. Zděděný člen musí být inicializován pomocí konstruktoru třídy nebo struktury.