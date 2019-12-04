---
title: Závažná chyba C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: 82a1a3e410505be53d4356e46d5521aebb72763c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756965"
---
# <a name="fatal-error-c1004"></a>Závažná chyba C1004

našel se neočekávaný konec souboru.

Kompilátor dosáhl konce zdrojového souboru bez překladu konstrukce. V kódu může chybět jeden z následujících elementů:

- Pravá složená závorka

- Pravá závorka

- Uzavírací značka komentáře (*/)

- Středník

Chcete-li tuto chybu vyřešit, ověřte následující:

- Výchozí disková jednotka nemá dostatek místa pro dočasné soubory, které vyžadují přibližně dvě místa jako zdrojový soubor.

- Direktiva `#if`, která je vyhodnocena jako false, nemá uzavírací direktivu `#endif`.

- Zdrojový soubor nekončí návratem na začátek řádku a řádkovým kanálem.

Následující ukázka generuje C1004:

```cpp
// C1004.cpp
#if TEST
int main() {}
// C1004
```

Možné řešení:

```cpp
// C1004b.cpp
#if TEST
#endif

int main() {}
```
