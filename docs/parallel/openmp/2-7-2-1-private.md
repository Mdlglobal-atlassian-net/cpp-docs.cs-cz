---
title: 2.7.2.1 privátní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d06650a784b5b59405f446f4701918393b21fa3b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387234"
---
# <a name="2721-private"></a>2.7.2.1 private

`private` Klauzule deklaruje proměnné v seznamu proměnné být privátní pro každé vlákno v týmu. Syntaxe `private` klauzule vypadá takto:

```
private(variable-list)
```

Chování zadané v proměnné `private` klauzule vypadá takto. Nový objekt s automatickým trváním úložiště přidělené konstrukce. Typ proměnné jsou určeny velikost a zarovnání nového objektu. Toto přidělení akce proběhne jednou pro každé vlákno v týmu a vyvolání výchozího konstruktoru pro objekt třídy v případě potřeby; jinak je neurčité počáteční hodnota.  Původní objekt odkazuje proměnná má neurčitá hodnota při vstupu do konstrukce, nesmí být upraveno v rámci dynamický rozsah konstrukce a má neurčitá hodnota při ukončení z konstrukce.

Lexikální rozsah direktiv konstrukce proměnná odkazuje na nový objekt privátní přidělené vláknu.

Omezení týkající `private` klauzule jsou následující:

- Proměnná typu třídy, který je zadán v `private` klauzule musí mít přístupná a jednoznačná výchozí konstruktor.

- Proměnnou podle `private` nesmí mít klauzuli **const**-kvalifikovaný typ, pouze pokud má třída typ s `mutable` člena.

- Zadané v proměnné `private` klauzule nesmí mít neúplný typ nebo typ odkazu.

- Proměnné, které se zobrazují v `reduction` klauzuli **paralelní** směrnice nelze zadat v `private` klauzuli direktivy sdílení práce, s vazbou na paralelní konstrukce.