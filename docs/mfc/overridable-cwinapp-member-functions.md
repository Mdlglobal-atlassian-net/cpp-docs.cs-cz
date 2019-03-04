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
ms.openlocfilehash: 35db009f86a0cb984f70a349a3ecdd93bfefb0f0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261242"
---
# <a name="overridable-cwinapp-member-functions"></a>Přepisovatelné členské funkce CWinApp

[CWinApp](../mfc/reference/cwinapp-class.md) poskytuje několik klíčů přepisovatelné členské funkce (`CWinApp` nahradí tyto členy ze třídy [CWinThread](../mfc/reference/cwinthread-class.md), ze kterého `CWinApp` odvozený):

- [InitInstance](../mfc/initinstance-member-function.md)

- [Spuštění](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [ONIDLE –](../mfc/onidle-member-function.md)

Jediná `CWinApp` je členská funkce, která je nutné přepsat `InitInstance`.

## <a name="see-also"></a>Viz také:

[CWinApp Třída aplikace](../mfc/cwinapp-the-application-class.md)
