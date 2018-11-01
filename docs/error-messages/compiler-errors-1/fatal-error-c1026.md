---
title: Závažná chyba C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: b1a659967a9a62cb79e1084f7d1fa1729bae14da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666184"
---
# <a name="fatal-error-c1026"></a>Závažná chyba C1026

přetečení zásobníku analyzátoru. program je moc složitý

Místo vyžadovaný pro analýzu program způsobila přetečení zásobníku kompilátoru.

Zjednodušte výrazů podle:

- Snížení úrovně vnoření v `for` a `switch` příkazy. Umístěte hlouběji vnořené příkazy do samostatné funkce.

- Rozdělení dlouhé výrazy zahrnující operátory čárkou nebo volání funkce.