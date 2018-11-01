---
title: Závažná chyba C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: 13fb8963b33569facf62ccedfe9ce8b7bbbbfdc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428116"
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