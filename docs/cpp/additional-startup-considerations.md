---
title: Další důležité informace o spuštění
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
ms.openlocfilehash: 16e48f2e4f7544d28a1bea00e1fdf2d1cff397b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605572"
---
# <a name="additional-startup-considerations"></a>Další důležité informace o spuštění

V jazyce C++ může tvorba a rušení objektů zahrnovat spouštění uživatelského kódu. Proto je důležité pochopit, kterým inicializacím dochází před vstupem do `main` a které destruktory jsou vyvolány po ukončení `main`. (Podrobné informace o tvorbě a rušení objektů naleznete v tématu [konstruktory](../cpp/constructors-cpp.md) a [destruktory](../cpp/destructors-cpp.md).)

Následujícím inicializacím dochází před vstupem do `main`:

- Výchozí inicializace statických dat na hodnotu nula. Všechna statická data bez explicitních inicializátorů jsou před spuštěním jakéhokoli jiného kódu nastaveny na hodnotu nula, včetně inicializací za běhu. Statické datové členy musí být explicitně definovány.

- Inicializace globálních statických objektů v jednotce převodu. K tomu může dojít buď před vstupem do `main` nebo před prvním použitím libovolné funkce nebo objektu v jednotce převodu daného objektu.

**Specifické pro Microsoft**

V programu Microsoft C++ jsou globální statické objekty inicializovány před vstupem do `main`.

**Specifické pro END Microsoft**

Globální statické objekty jsou vzájemně závislé, v jiných jednotkách převodu však mohou zapříčinit nesprávné chování.

## <a name="see-also"></a>Viz také:

[Spuštění a ukončení](../cpp/startup-and-termination-cpp.md)