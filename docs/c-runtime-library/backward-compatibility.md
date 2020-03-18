---
title: Zpětná kompatibilita
ms.date: 11/04/2016
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
ms.openlocfilehash: 2c2b4570e5e3131911e7f424280f16e9977f047e
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438560"
---
# <a name="backward-compatibility"></a>Zpětná kompatibilita

Z důvodu kompatibility mezi verzemi produktu OLDNAMES knihovny. LIB mapuje staré názvy na nové názvy. `open` například mapuje na `_open`. Musíte explicitně propojit s OLDNAMES. LIB pouze při kompilaci s následujícími kombinacemi možností příkazového řádku:

- `/Zl` (vynechání názvu výchozí knihovny ze souboru objektů) a `/Ze` (výchozí – použít rozšíření Microsoftu)

- `/link` (ovládací prvek Linker), `/NOD` (bez vyhledávání výchozích knihoven) a `/Ze`

Další informace o možnostech příkazového řádku kompilátoru naleznete v tématu [Reference k kompilátoru](../build/reference/compiler-options.md).

## <a name="see-also"></a>Viz také

[Kompatibilita](../c-runtime-library/compatibility.md)
