---
title: Priorita odvozených pravidel
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: 99d92985b00f7c05f409b43009eb61cec6d6f1b1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413274"
---
# <a name="precedence-in-inference-rules"></a>Priorita odvozených pravidel

Pokud odvozené pravidlo je definovaná víckrát, používá NMAKE definici nejvyšší prioritu. Následující seznam uvádí pořadí dle priority od nejvyšší po nejnižší:

1. Pravidlo odvození definované v souboru pravidel; novější definice mají přednost.

1. Pravidlo odvození podle Tools.ini; novější definice mají přednost.

1. Předdefinované odvozené pravidlo.

## <a name="see-also"></a>Viz také:

[Odvozená pravidla](../build/inference-rules.md)
