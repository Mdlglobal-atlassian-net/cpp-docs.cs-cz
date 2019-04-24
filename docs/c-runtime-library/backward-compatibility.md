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
ms.openlocfilehash: f672f0601a9d20a726f90963265d08ec212dedce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290362"
---
# <a name="backward-compatibility"></a>Zpětná kompatibilita

Kvůli kompatibilitě mezi verzemi tohoto produktu, knihovna OLDNAMES. LIB mapuje starých názvů na nové názvy. Například `open` mapuje `_open`. Je třeba explicitně propojit s OLDNAMES. LIB jenom při kompilaci s následující kombinace možností příkazového řádku:

- `/Zl` (vypuštění názvu výchozí knihovny ze souboru objektu) a `/Ze` (výchozí nastavení – pomocí rozšíření společnosti Microsoft)

- `/link` (linkeru – ovládací prvek), `/NOD` (hledání žádné výchozí knihovny), a `/Ze`

Další informace o možnostech příkazového řádku kompilátoru najdete v tématu [kompilátory](../build/reference/compiler-options.md).

## <a name="see-also"></a>Viz také:

[Kompatibilita](../c-runtime-library/compatibility.md)
