---
title: 2.7 datové prostředí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17c60c621defa15c034f57d0af8f14637db54f03
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378134"
---
# <a name="27-data-environment"></a>2.7 Datové prostředí

Tato část představuje direktivu a několik klauzulí pro řízení prostředí dat během provádění paralelních oblastí, následujícím způsobem:

- A **threadprivate** – direktiva (viz následující část) je k dispozici tak, aby rozsahu souboru, rozsahu oboru názvů nebo oboru bloku statických proměnných místního vlákna.

- Klauzule, které může být určen direktivami řízení sdílení atributy proměnné po dobu trvání konstrukce paralelní nebo sdílení práce jsou popsány v [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.