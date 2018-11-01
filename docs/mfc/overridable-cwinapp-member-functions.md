---
title: Přepisovatelné členské funkce CWinApp
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 9f1098e305606df9463e308466b7864b019d5a00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459277"
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
