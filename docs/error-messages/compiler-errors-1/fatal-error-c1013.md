---
title: Závažná chyba C1013 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1013
dev_langs:
- C++
helpviewer_keywords:
- C1013
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33c10062cac83984fb1c68835780497b89c4cbc1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050508"
---
# <a name="fatal-error-c1013"></a>Závažná chyba C1013

limit kompilátoru: moc velký počet levých závorek

Výraz obsahuje příliš mnoho úrovní závorky v jednom výrazu. Zjednodušit výraz nebo ho rozdělte do více příkazů.

Před Visual C++ 6.0 aktualizací Service Pack 3 byl překročen limit na vnořené závorky v jednom výrazu 59. V současné době limitu vnořené závorky je 256.