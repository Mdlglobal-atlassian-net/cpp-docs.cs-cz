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
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744472"
---
# <a name="backward-compatibility"></a>Zpětná kompatibilita

Kvůli kompatibilitě mezi verzemi tohoto produktu, knihovna OLDNAMES. LIB mapuje starých názvů na nové názvy. Například `open` mapuje `_open`. Je třeba explicitně propojit s OLDNAMES. LIB jenom při kompilaci s následující kombinace možností příkazového řádku:

- `/Zl` (vypuštění názvu výchozí knihovny ze souboru objektu) a `/Ze` (výchozí nastavení – pomocí rozšíření společnosti Microsoft)

- `/link` (linkeru – ovládací prvek), `/NOD` (hledání žádné výchozí knihovny), a `/Ze`

Další informace o možnostech příkazového řádku kompilátoru najdete v tématu [kompilátory](../build/reference/compiler-options.md).

## <a name="see-also"></a>Viz také:

[Kompatibilita](../c-runtime-library/compatibility.md)
