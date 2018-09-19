---
title: 2.7.2.5 výchozí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 047110fe80d15d0ff3d979eeec8abf3e42dc35f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401560"
---
# <a name="2725-default"></a>2.7.2.5 default

**Výchozí** klauzule umožňuje uživateli ovlivňují atributy sdílení dat z proměnných. Syntaxe **výchozí** klauzule vypadá takto:

```
default(shared | none)
```

Určení **default(shared)** odpovídá explicitně uvedete seznam jednotlivých aktuálně viditelné proměnné v **sdílené** klauzule, pokud se nejedná **threadprivate** nebo **nevýhody**`t`-kvalifikovaný. Chybí explicitní **výchozí** klauzule, výchozí chování je stejné jako if **default(shared)** byly zadány.

Určení **default(none)** vyžaduje, aby aspoň jeden z následujících musí mít hodnotu true pro každý odkaz na proměnnou v lexikálním rozsahu paralelní konstrukce:

- Proměnná je explicitně uvedená v klauzuli data-sharing atribut konstruktoru, který obsahuje odkaz na.

- Proměnná je deklarována v rámci paralelní konstrukce.

- Proměnná je **threadprivate**.

- Obsahuje proměnnou **const**-kvalifikovaný typ.

- Proměnná je řídicí proměnná smyčky pro **pro** smyčku, která bezprostředně následuje po **pro** nebo **paralelní pro** směrnice a reference proměnné se zobrazí uvnitř smyčka .

Určení proměnné na **firstprivate**, **lastprivate**, nebo **snížení** klauzule uzavřené směrnice způsobí, že implicitní odkaz na proměnnou v značka kontext. Tyto odkazy jsou implicitní jsou také v souladu s požadavky uvedené výše.

Pouze jeden **výchozí** může být zadána klauzule na **paralelní** směrnice.

Sdílení dat atribut lze přepsat pomocí výchozí proměnné **privátní**, **firstprivate**, **lastprivate**, **snížení**, a **sdílené** klauzule, jak je ukázáno v následujícím příkladu:

```
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```