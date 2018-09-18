---
title: Závažná chyba nástroje NMAKE U1064 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1064
dev_langs:
- C++
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4240bf2c553957e73d5ead0bdd03ea129450645b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092996"
---
# <a name="nmake-fatal-error-u1064"></a>Závažná chyba nástroje NMAKE U1064

Nenašel se soubor MAKEFILE a není zadaný žádný cíl

NMAKE příkazového řádku nezadali souboru pravidel nebo cíl a aktuální adresář neobsahuje soubor s názvem souboru pravidel.

NMAKE vyžaduje souboru pravidel nebo příkazového řádku cíl (nebo obojí). Chcete-li zpřístupnit souboru pravidel NMAKE, možnost /F nebo umístit soubor s názvem souboru pravidel v aktuálním adresáři. NMAKE můžete vytvořit cíl příkazového řádku pomocí pravidla odvození, pokud není k dispozici soubor pravidel.