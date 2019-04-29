---
title: Závažná chyba C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 988842a0d5e8002ffd1478a2e10a8c88ee971911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397494"
---
# <a name="fatal-error-c1305"></a>Závažná chyba C1305

profilové databáze 'pgd_file' je pro jinou architekturu.

Soubor .pgd, který byl vytvořen /LTCG:PGINSTRUMENT operace pro jinou platformu byl předán [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optimalizace na základě profilu](../../build/profile-guided-optimizations.md) jsou dostupné pro x86 a x64 platformy. Soubor .pgd generuje s použitím operace jedna platforma, která /LTCG:PGINSTRUMENT však není platný jako vstup pro /LTCG:PGOPTIMIZE pro různé platformy.

Chcete-li vyřešit tuto chybu, předejte pouze soubor .pgd, který je vytvořen s /LTCG:PGINSTRUMENT k /LTCG:PGOPTIMIZE v rámci téže platformy.