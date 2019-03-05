---
title: Jaké jsou náklady na odvození třídy z objektu CObject?
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: de760a2fd2908595314dc09cf5a317da3581e3bb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326384"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>Jaké jsou náklady na odvození třídy z objektu CObject?

Režie při odvozování od třídy [CObject](../mfc/reference/cobject-class.md) je minimální. Pouze čtyři virtuální funkce a jediného nastavení dědí odvozená třída [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objektu.

## <a name="see-also"></a>Viz také:

[CObject – třída: Nejčastější dotazy](../mfc/cobject-class-frequently-asked-questions.md)
