---
title: 2.7 Datové prostředí
ms.date: 11/04/2016
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
ms.openlocfilehash: b65dfc7d7694b36ef4f89351579cd73e07ab537c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491962"
---
# <a name="27-data-environment"></a>2.7 Datové prostředí

Tato část představuje direktivu a několik klauzulí pro řízení prostředí dat během provádění paralelních oblastí, následujícím způsobem:

- A **threadprivate** – direktiva (viz následující část) je k dispozici tak, aby rozsahu souboru, rozsahu oboru názvů nebo oboru bloku statických proměnných místního vlákna.

- Klauzule, které může být určen direktivami řízení sdílení atributy proměnné po dobu trvání konstrukce paralelní nebo sdílení práce jsou popsány v [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.