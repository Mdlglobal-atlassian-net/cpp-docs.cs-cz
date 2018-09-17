---
title: Priorita odvozených pravidel | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4f2e7ff55e935b7e425b552ba85f47f134c6b80
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725228"
---
# <a name="precedence-in-inference-rules"></a>Priorita odvozených pravidel

Pokud odvozené pravidlo je definovaná víckrát, používá NMAKE definici nejvyšší prioritu. Následující seznam uvádí pořadí dle priority od nejvyšší po nejnižší:

1. Pravidlo odvození definované v souboru pravidel; novější definice mají přednost.

1. Pravidlo odvození podle Tools.ini; novější definice mají přednost.

1. Předdefinované odvozené pravidlo.

## <a name="see-also"></a>Viz také

[Odvozená pravidla](../build/inference-rules.md)