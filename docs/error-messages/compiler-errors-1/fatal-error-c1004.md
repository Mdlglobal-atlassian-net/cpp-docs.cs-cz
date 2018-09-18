---
title: Závažná chyba C1004 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1004
dev_langs:
- C++
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a284de510fde49602a06fb9282c0ddd59eeb0ac1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020277"
---
# <a name="fatal-error-c1004"></a>Závažná chyba C1004

Neočekávaný konec souboru nalezen

Kompilátor bylo dosaženo konce zdrojového souboru bez překladu konstrukci. Kód pravděpodobně chybí jeden z následujících elementů:

- Pravé složené závorky

- Pravá závorka

- Na závěr komentáře značky (* /)

- Středníkem

Chcete-li tuto chybu vyřešit, zkontrolujte následující:

- Na disk výchozí nemá dostatek místa pro dočasné soubory, které vyžadují dvakrát tolik místa jako zdrojový soubor.

- `#if` Direktiva, která se vyhodnotí jako false chybí uzavírací `#endif` směrnice.

- Zdrojový soubor nesmí končit zalomení řádku a odřádkování.

Následující ukázka generuje C1004:

```
// C1004.cpp
#if TEST
int main() {}
// C1004
```

Možná řešení:

```
// C1004b.cpp
#if TEST
#endif

int main() {}
```