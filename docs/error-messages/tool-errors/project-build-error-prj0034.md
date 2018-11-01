---
title: Chyba sestavení projektu PRJ0034
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: 7c078a3d2aef24df9151cb10f81c1b7423809e68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549055"
---
# <a name="project-build-error-prj0034"></a>Chyba sestavení projektu PRJ0034

Vlastnost "Additional Dependencies" vlastního na úrovni projektu sestavení krok obsažené "makra" která je vyhodnocena na "macro_expansion".

Vlastní krok sestavení na projektu obsahovala chybu v jeho další závislosti, pravděpodobně z důvodu problému vyhodnocení makra. Tato chyba může také znamenat, že cesta je chybně vytvořený kód, obsahující znaky nebo kombinace znaků, které jsou neplatné v cestě k souboru.

Chcete-li tuto chybu vyřešit, opravte makro nebo odstraňte specifikaci cesty. Vyhodnocená cesta je absolutní cesta z adresáře projektu.