---
title: Závažná chyba C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: a7c7a5da01c8b4a44c307a00f53530acb12a8009
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204650"
---
# <a name="fatal-error-c1026"></a>Závažná chyba C1026

přetečení zásobníku analyzátoru, program je moc složitý.

Prostor vyžadovaný k analýze programu způsobil přetečení zásobníku kompilátoru.

Snižte složitost výrazů o:

- Snížení vnořování v příkazech `for` a `switch`. Do samostatných funkcí vložte více hluboko vnořených příkazů.

- Rozdělení dlouhých výrazů, které zahrnují operátory čárky nebo volání funkcí.
