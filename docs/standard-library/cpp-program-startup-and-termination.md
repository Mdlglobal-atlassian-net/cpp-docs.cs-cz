---
title: Spuštění a ukončení programu C++
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
ms.openlocfilehash: e59e8852172a998e4bf4f42f9f919dc29c2ded85
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450656"
---
# <a name="c-program-startup-and-termination"></a>Spuštění a ukončení programu C++

C++ Program provádí stejné operace jako program v jazyce C při spuštění programu a ukončení programu a ještě více popsaných zde.

Předtím, než cílový prostředí zavolá `main`funkci a po uložení všech konstantních počátečních hodnot, které zadáte ve všech objektech, které mají statickou dobu trvání, program provede všechny zbývající konstruktory těchto statických objektů. Pořadí provádění není zadáno mezi jednotkami překladu, ale můžete předpokládat, že některé objekty [iostreams](../standard-library/iostreams-conventions.md) jsou správně inicializovány pro použití těmito statickými konstruktory. Tyto řídicí textové datové proudy jsou:

- [CIN](../standard-library/iostream.md#cin) – pro standardní vstup.

- [cout](../standard-library/iostream.md#cout) – pro standardní výstup.

- [cerr](../standard-library/iostream.md#cerr) – pro standardní chybový výstup bez vyrovnávací paměti.

- [CLOG](../standard-library/iostream.md#clog) – pro standardní chybový výstup v bufferu.

Tyto objekty lze použít také v rámci destruktorů, které jsou volány pro statické objekty během ukončení programu.

Stejně jako u jazyka C vrací `main` `atexit` volání nebo `exit` volání všech funkcí zaregistrovaných v v obráceném pořadí registru. Výjimka vyvolaná z takových volání `terminate`zaregistrovaných funkcí.

## <a name="see-also"></a>Viz také:

[C++Přehled standardní knihovny](../standard-library/cpp-standard-library-overview.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
