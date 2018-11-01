---
title: 2.7.2 Klauzule atributů pro sdílení dat
ms.date: 11/04/2016
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
ms.openlocfilehash: 4c9209a4d627c6212087b621b223a3fb81b48ce3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559650"
---
# <a name="272-data-sharing-attribute-clauses"></a>2.7.2 Klauzule atributů pro sdílení dat

Několik direktivy přijmout klauzule, které umožní uživateli řídit sdílení atributy proměnné po dobu trvání oblast. Sdílení klauzule atributů pro platí pouze pro proměnné v lexikálním rozsahu direktiva, na kterém se zobrazí v klauzuli. Některé z následujících doložek jsou povolené pro všechny direktivy. Seznam klauzule, které jsou platné pro konkrétní direktivu jsou popsány s direktivou.

Pokud je proměnná viditelná, když paralelní nebo dochází v konstruktoru work-sharing a proměnná není zadán v klauzuli sdílení atribut nebo **threadprivate** direktiv, pak proměnná se sdílí. Jsou sdílené statické proměnné deklarované v rámci dynamický rozsah paralelní oblasti. Přidělené paměti haldy (například pomocí **malloc()** v jazyce C nebo C++ nebo **nové** operátor v jazyce C++) se sdílí. (Ukazatel na tuto paměť, ale může být buď privátní nebo sdílený.) Proměnné s automatickým trváním úložiště deklarované v rámci dynamický rozsah paralelní oblasti jsou privátní.

Většina klauzulí přijmout *seznamu proměnné* argument, který je čárkou oddělený seznam proměnných, které jsou viditelné. Pokud proměnná odkazuje na atribut klauzuli data-sharing se typu odvozeného ze šablony a neexistují žádné odkazy na tuto proměnnou v programu, není chování definováno.

Všechny proměnné, které se zobrazují v klauzulích direktiv musí být viditelná. Klauzule může opakovat podle potřeby, ale žádná proměnná je možné zadat více než jednu klauzuli, s tím rozdílem, že proměnné lze v obou **firstprivate** a **lastprivate** klauzuli.

Klauzule atributů pro sdílení dat v následujících částech:

- **privátní**, [části 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stránce 25.

- **firstprivate**, [části 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) na stránce 26.

- **lastprivate**, [části 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) na stránce 27.

- **sdílené**, [části 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) na stránce 27.

- **výchozí**, [části 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md) na stránce 28.

- **snížení**, [části 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md) na stránce 28.

- **copyin**, [části 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md) na stránce 31.

- **copyprivate**, [části 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) na stránce 32.