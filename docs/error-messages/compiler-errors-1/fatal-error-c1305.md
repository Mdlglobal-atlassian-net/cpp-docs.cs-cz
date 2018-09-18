---
title: Závažná chyba C1305 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1305
dev_langs:
- C++
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4beb1140d161b8cbe54cab40dcc72899c976edc3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048744"
---
# <a name="fatal-error-c1305"></a>Závažná chyba C1305

profilové databáze 'pgd_file' je pro jinou architekturu.

Soubor .pgd, který byl vytvořen /LTCG:PGINSTRUMENT operace pro jinou platformu byl předán [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md) jsou dostupné pro x86 a x64 platformy. Soubor .pgd generuje s použitím operace jedna platforma, která /LTCG:PGINSTRUMENT však není platný jako vstup pro /LTCG:PGOPTIMIZE pro různé platformy.

Chcete-li vyřešit tuto chybu, předejte pouze soubor .pgd, který je vytvořen s /LTCG:PGINSTRUMENT k /LTCG:PGOPTIMIZE v rámci téže platformy.