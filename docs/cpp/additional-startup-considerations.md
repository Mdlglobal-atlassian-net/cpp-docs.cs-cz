---
title: Důležité informace o dalších spuštění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d629451161d94853558887eb7029fc165d13d9b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079216"
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