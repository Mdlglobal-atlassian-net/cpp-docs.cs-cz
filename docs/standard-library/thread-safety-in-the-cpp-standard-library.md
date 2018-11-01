---
title: Bezpečný přístup z více vláken ve standardní knihovně C++
ms.date: 11/04/2016
helpviewer_keywords:
- thread safety
- C++ Standard Library, thread safety
- thread safety, C++ Standard Library
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
ms.openlocfilehash: 27ac930e567521b12dfc35e2f8c4c389c35ae47d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607633"
---
# <a name="thread-safety-in-the-c-standard-library"></a>Bezpečný přístup z více vláken ve standardní knihovně C++

Platí následující pravidla bezpečný přístup z více vláken na všechny třídy ve standardní knihovně C++ – jedná se o `shared_ptr`, jak je popsáno níže.  Někdy jsou k dispozici větší záruku – třeba standardní iostream – objekty, jak je popsáno níže a typy určený speciálně pro multithreading, jako ty v [ \<atomické >](../standard-library/atomic.md).

Objekt je bezpečná pro vlákno pro čtení z více vláken. Například daný objekt A je bezpečné A z vlákna 1 a čtení z vlákna 2 současně.

Pokud objekt se zápisem do jedním vláknem, pak všechny čte a zapisuje do tohoto objektu na stejné nebo jiných vláken musí být chráněné. Například zadaný objekt A, pokud vlákno 1 zapisuje do A, pak vlákno 2 musí být zabránily čtení nebo zápisu do A.

Je bezpečné ke čtení a zápisu na jednu instanci typu, přestože jiné vlákno je čtení a zápis do jiné instance stejného typu. Například s ohledem objekty A a B stejného typu, je bezpečné při ve vlákně 1 se zápisem A a B je čten ve vlákně 2.

## <a name="sharedptr"></a>shared_ptr

Více vláken může současně číst a zapisovat různé [shared_ptr](../standard-library/shared-ptr-class.md) objektů, i když jsou objekty kopie, které sdílejí vlastnictví.

## <a name="iostream"></a>iostream

Iostream – standardní objekty `cin`, `cout`, `cerr`, `clog`, `wcin`, `wcout`, `wcerr`, a `wclog` řídit stejnými pravidly jako ostatní třídy, s touto výjimkou: je bezpečné zápis do objektu z více vláken. Například může zapisovat vlákno 1 [cout](../standard-library/iostream.md#cout) ve stejnou dobu jako vlákno 2. Nicméně to může způsobit výstup ze dvou vláken být Smíšeného.

> [!NOTE]
> Čtení z vyrovnávací paměti datového proudu se nepovažuje za operace čtení. Místo toho bude považován být operace zápisu, protože se změnil stav třídy.

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
