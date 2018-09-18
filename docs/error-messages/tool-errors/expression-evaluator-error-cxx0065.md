---
title: Vyhodnocování výrazu CXX0065 chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c100b1edbd36f4384e8deb1abf5b36465e8da479
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024161"
---
# <a name="expression-evaluator-error-cxx0065"></a>Chyba při vyhodnocování výrazu CXX0065

Proměnná musí rámec zásobníku

Výraz obsahuje proměnné, která existuje v aktuálním oboru, ale ještě nebyl vytvořen.

Této chybě může dojít, když jste vkročili prologu funkce ale ještě není nastavení rámce zásobníku pro funkci, nebo pokud jste vkročili ukončovací kód pro funkci.

Krokovat kód prologu, dokud rámce zásobníku je nastavený před vyhodnocením výrazu.

Tato chyba se shoduje s CAN0065.