---
title: Závažná chyba nástroje NMAKE U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: 71213391032989e5faf8889761b29194928125a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463359"
---
# <a name="nmake-fatal-error-u1064"></a>Závažná chyba nástroje NMAKE U1064

Nenašel se soubor MAKEFILE a není zadaný žádný cíl

NMAKE příkazového řádku nezadali souboru pravidel nebo cíl a aktuální adresář neobsahuje soubor s názvem souboru pravidel.

NMAKE vyžaduje souboru pravidel nebo příkazového řádku cíl (nebo obojí). Chcete-li zpřístupnit souboru pravidel NMAKE, možnost /F nebo umístit soubor s názvem souboru pravidel v aktuálním adresáři. NMAKE můžete vytvořit cíl příkazového řádku pomocí pravidla odvození, pokud není k dispozici soubor pravidel.