---
title: Zpětná kompatibilita
ms.date: 11/04/2016
f1_keywords:
- c.programs
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
ms.openlocfilehash: d418a3450f22e53c8cb320f0a1a27c9f2e434c54
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460551"
---
# <a name="backward-compatibility"></a>Zpětná kompatibilita

Kvůli kompatibilitě mezi verzemi tohoto produktu, knihovna OLDNAMES. LIB mapuje starých názvů na nové názvy. Například `open` mapuje `_open`. Je třeba explicitně propojit s OLDNAMES. LIB jenom při kompilaci s následující kombinace možností příkazového řádku:

- `/Zl` (vypuštění názvu výchozí knihovny ze souboru objektu) a `/Ze` (výchozí nastavení – pomocí rozšíření společnosti Microsoft)

- `/link` (linkeru – ovládací prvek), `/NOD` (hledání žádné výchozí knihovny), a `/Ze`

Další informace o možnostech příkazového řádku kompilátoru najdete v tématu [kompilátory](../build/reference/compiler-options.md).

## <a name="see-also"></a>Viz také

[Kompatibilita](../c-runtime-library/compatibility.md)