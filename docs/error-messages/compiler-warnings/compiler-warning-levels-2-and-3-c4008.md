---
title: Upozornění kompilátoru (úrovně 2 a 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 9b6fb56045d53cd18689f3903bb3d7a08c3d4e4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198001"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Upozornění kompilátoru (úrovně 2 a 3) C4008

' identifier ': atribut ' atribut ' byl ignorován

Kompilátor ignoroval atribut `__fastcall`, **static**nebo **inline** pro funkci (upozornění úrovně 3) nebo data (upozornění úrovně 2).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. `__fastcall` atribut s daty.

1. **statický** nebo **vložený** atribut s **hlavní** funkcí
