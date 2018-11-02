---
title: Jaké jsou náklady na odvození třídy z objektu CObject?
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: 521b6a32e3e5b34b4da9dab3117d55a728bd8e88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500445"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>Jaké jsou náklady na odvození třídy z objektu CObject?

Režie při odvozování od třídy [CObject](../mfc/reference/cobject-class.md) je minimální. Pouze čtyři virtuální funkce a jediného nastavení dědí odvozená třída [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objektu.

## <a name="see-also"></a>Viz také

[CObject – třída: Nejčastější dotazy](../mfc/cobject-class-frequently-asked-questions.md)
