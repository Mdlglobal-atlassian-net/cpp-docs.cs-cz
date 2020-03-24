---
title: Závažná chyba C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 6ad00eb3d95e9f09d4f84daefb7e2a87fd1a3abf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203356"
---
# <a name="fatal-error-c1305"></a>Závažná chyba C1305

profilová databáze ' pgd_file ' je určena pro jinou architekturu

Soubor. PGD, který byl vygenerován z operace/LTCG: PGINSTRUMENT pro jinou platformu, byl předán do [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optimalizace](../../build/profile-guided-optimizations.md) na základě profilu jsou k dispozici pro platformy x86 a x64. Soubor. pgd generovaný pomocí operace/LTCG: PGINSTRUMENT pro jednu platformu ale není platný jako vstup do/LTCG: PGOPTIMIZE pro jinou platformu.

Chcete-li tuto chybu vyřešit, předejte pouze soubor. PGD, který je vytvořen pomocí/LTCG: PGINSTRUMENT na/LTCG: PGOPTIMIZE na stejné platformě.
