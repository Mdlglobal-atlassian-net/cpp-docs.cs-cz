---
title: Přepisovatelné členské funkce CWinApp | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ced9d7d5f7f49df50e028a299f83ddebdc9fc2d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395119"
---
# <a name="overridable-cwinapp-member-functions"></a>Přepisovatelné členské funkce CWinApp

[CWinApp](../mfc/reference/cwinapp-class.md) poskytuje několik klíčů přepisovatelné členské funkce (`CWinApp` nahradí tyto členy ze třídy [CWinThread](../mfc/reference/cwinthread-class.md), ze kterého `CWinApp` odvozený):

- [InitInstance –](../mfc/initinstance-member-function.md)

- [Spuštění](../mfc/run-member-function.md)

- [ExitInstance –](../mfc/exitinstance-member-function.md)

- [ONIDLE –](../mfc/onidle-member-function.md)

Jediná `CWinApp` je členská funkce, která je nutné přepsat `InitInstance`.

## <a name="see-also"></a>Viz také

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
