---
title: Priorita odvozených pravidel
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: ca24134fd1829ad3d97ca67b8c30aae3af4109ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319678"
---
# <a name="precedence-in-inference-rules"></a>Priorita odvozených pravidel

Pokud odvozené pravidlo je definovaná víckrát, používá NMAKE definici nejvyšší prioritu. Následující seznam uvádí pořadí dle priority od nejvyšší po nejnižší:

1. Pravidlo odvození definované v souboru pravidel; novější definice mají přednost.

1. Pravidlo odvození podle Tools.ini; novější definice mají přednost.

1. Předdefinované odvozené pravidlo.

## <a name="see-also"></a>Viz také:

[Odvozená pravidla](inference-rules.md)
