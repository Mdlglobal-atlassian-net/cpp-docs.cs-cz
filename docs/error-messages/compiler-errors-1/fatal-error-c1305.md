---
title: Závažná chyba C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: d67f0eabfd0718d8a3e3dd75e96c3e6c0d2266b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623207"
---
# <a name="fatal-error-c1305"></a>Závažná chyba C1305

profilové databáze 'pgd_file' je pro jinou architekturu.

Soubor .pgd, který byl vytvořen /LTCG:PGINSTRUMENT operace pro jinou platformu byl předán [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md) jsou dostupné pro x86 a x64 platformy. Soubor .pgd generuje s použitím operace jedna platforma, která /LTCG:PGINSTRUMENT však není platný jako vstup pro /LTCG:PGOPTIMIZE pro různé platformy.

Chcete-li vyřešit tuto chybu, předejte pouze soubor .pgd, který je vytvořen s /LTCG:PGINSTRUMENT k /LTCG:PGOPTIMIZE v rámci téže platformy.