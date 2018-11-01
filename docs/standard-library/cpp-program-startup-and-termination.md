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
ms.openlocfilehash: 2246e50c81da9eb505fd30cfa31f9f24e3fe4703
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459186"
---
# <a name="c-program-startup-and-termination"></a>Spuštění a ukončení programu C++

Program jazyka C++ provede stejné operace jako při spuštění programu a při ukončení programu a navíc několik více podle zde uvedeného programu jazyka C.

Před cílové prostředí volá funkci `main`, a po ukládá všechny konstantní počáteční hodnoty zadáte všechny objekty, které mají statické trvání, program se spustí všechny zbývající konstruktory pro taková statických objektů. Pořadí provádění není určena mezi jednotkami překladu, ale je můžete přesto předpokládat, že některé [iostreams](../standard-library/iostreams-conventions.md) objekty jsou správně inicializovány pro použití těchto statické konstruktory. Tyto ovládací prvek textové datové proudy jsou:

- [CIN](../standard-library/iostream.md#cin) – pro standardní vstup.

- [cout](../standard-library/iostream.md#cout) – pro standardní výstup.

- [cerr](../standard-library/iostream.md#cerr) – pro bez vyrovnávací paměti standardní chybový výstup.

- [clog](../standard-library/iostream.md#clog) – pro vyrovnávací paměť standardní chybový výstup.

Můžete také použít tyto objekty v rámci destruktory pro statické objekty, volá se při ukončení programu.

Stejně jako u C, vrácení z `main` nebo volání `exit` volá všechny funkce zaregistrovaného `atexit` v obráceném pořadí z registru. Výjimka vyvolaná z těchto registrovaných funkce volá `terminate`.

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
