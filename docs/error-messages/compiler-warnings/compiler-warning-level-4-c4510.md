---
title: Upozornění kompilátoru (úroveň 4) C4510
description: Upozornění kompilátoru C4510 popis a řešení.
ms.date: 09/22/2019
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: 05a6d0fe42d8247d3328506d8772b2fa77b5703c
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230385"
---
# <a name="compiler-warning-level-4-c4510"></a>Upozornění kompilátoru (úroveň 4) C4510

> '*Class*': Nepodařilo se vygenerovat výchozí konstruktor.

Kompilátor nemůže vygenerovat výchozí konstruktor pro určenou třídu, která nemá žádné uživatelsky definované konstruktory. Objekty tohoto typu nelze vytvořit.

Existuje několik situací, které brání kompilátoru v generování výchozího konstruktoru, včetně:

- Datový člen **const** .

- Datový člen, který je odkazem.

Chcete-li tento problém vyřešit, vytvořte uživatelsky definovaný výchozí konstruktor pro třídu, která inicializuje tyto členy.
