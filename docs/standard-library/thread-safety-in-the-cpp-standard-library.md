---
title: Bezpečný přístup z více vláken ve standardní knihovně C++
ms.date: 11/04/2016
helpviewer_keywords:
- thread safety
- C++ Standard Library, thread safety
- thread safety, C++ Standard Library
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
ms.openlocfilehash: 4ac029a119a77fa87c6cd004fece9c4e6b382026
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460068"
---
# <a name="thread-safety-in-the-c-standard-library"></a>Bezpečný přístup z více vláken ve standardní knihovně C++

Následující pravidla zabezpečení vlákna se vztahují na všechny třídy ve C++ standardní knihovně – to zahrnuje `shared_ptr`, jak je popsáno níže.  Jsou někdy k dispozici silnější záruky, například standardní objekty iostream –, jak je popsáno níže, a typy určené speciálně pro multithreading, podobně jako ty v [ \<atomických >](../standard-library/atomic.md).

Objekt je pro čtení z více vláken bezpečný pro přístup z více vláken. Například s ohledem na objekt A je bezpečné číst z vlákna 1 a z vlákna 2 současně.

Pokud je do objektu zapisováno v jednom vlákně, musí být všechny operace čtení a zápisu do tohoto objektu ve stejném nebo jiném vlákně chráněny. Například s ohledem na objekt A, pokud vlákno 1 zapisuje do, pak musí být vlákno 2 znemožněno čtení nebo zápis do.

Čtení a zápis do jedné instance typu je bezpečné i v případě, že jiné vlákno čte nebo zapisuje do jiné instance stejného typu. Například vzhledem k tomu, že dané objekty a a B stejného typu jsou v bezpečí při zápisu do vlákna 1 a B čteny ve vláknu 2.

## <a name="sharedptr"></a>shared_ptr

Více vláken může současně číst a zapisovat různé objekty [shared_ptr](../standard-library/shared-ptr-class.md) , i když jsou objekty kopírovány, které sdílejí vlastnictví.

## <a name="iostream"></a>iostream

Standardní objekty `cin`iostream – ,`wcerr`, `cout` ,`clog` ,,`wclog` , a dodržují stejná pravidla jako ostatní třídy, s touto výjimkou: je bezpečné `wcin` `cerr` `wcout` zápis do objektu z více vláken. Například vlákno 1 může zapisovat do [cout](../standard-library/iostream.md#cout) ve stejnou dobu jako vlákno 2. To však může způsobit vzájemnou kombinaci výstupu z těchto dvou vláken.

> [!NOTE]
> Čtení z vyrovnávací paměti datového proudu se nepovažuje za operaci čtení. Místo toho se považuje za operaci zápisu, protože stav třídy je změněn.

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)
