---
title: Priorita odvozených pravidel
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: 30dee54c99115c076f7662bafb8aa22d97f234fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548730"
---
# <a name="precedence-in-inference-rules"></a>Priorita odvozených pravidel

Pokud odvozené pravidlo je definovaná víckrát, používá NMAKE definici nejvyšší prioritu. Následující seznam uvádí pořadí dle priority od nejvyšší po nejnižší:

1. Pravidlo odvození definované v souboru pravidel; novější definice mají přednost.

1. Pravidlo odvození podle Tools.ini; novější definice mají přednost.

1. Předdefinované odvozené pravidlo.

## <a name="see-also"></a>Viz také

[Odvozená pravidla](../build/inference-rules.md)