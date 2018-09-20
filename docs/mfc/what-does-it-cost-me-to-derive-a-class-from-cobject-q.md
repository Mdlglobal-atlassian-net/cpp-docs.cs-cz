---
title: Jaké jsou náklady na odvození třídy z objektu CObject? | Dokumenty Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e41f9060ce24b89a0a7faae54ca6207c740475f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443238"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>Jaké jsou náklady na odvození třídy z objektu CObject?

Režie při odvozování od třídy [CObject](../mfc/reference/cobject-class.md) je minimální. Pouze čtyři virtuální funkce a jediného nastavení dědí odvozená třída [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objektu.

## <a name="see-also"></a>Viz také

[CObject – třída: Nejčastější dotazy](../mfc/cobject-class-frequently-asked-questions.md)
