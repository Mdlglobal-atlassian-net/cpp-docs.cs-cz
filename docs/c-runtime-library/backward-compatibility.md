---
title: Zpětná kompatibilita | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3056b90f3c6f0f62158a9b6dcfe145cda9740c6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092190"
---
# <a name="backward-compatibility"></a>Zpětná kompatibilita

Kvůli kompatibilitě mezi verzemi tohoto produktu, knihovna OLDNAMES. LIB mapuje starých názvů na nové názvy. Například `open` mapuje `_open`. Je třeba explicitně propojit s OLDNAMES. LIB jenom při kompilaci s následující kombinace možností příkazového řádku:

- `/Zl` (vypuštění názvu výchozí knihovny ze souboru objektu) a `/Ze` (výchozí nastavení – pomocí rozšíření společnosti Microsoft)

- `/link` (linkeru – ovládací prvek), `/NOD` (hledání žádné výchozí knihovny), a `/Ze`

Další informace o možnostech příkazového řádku kompilátoru najdete v tématu [kompilátory](../build/reference/compiler-options.md).

## <a name="see-also"></a>Viz také

[Kompatibilita](../c-runtime-library/compatibility.md)