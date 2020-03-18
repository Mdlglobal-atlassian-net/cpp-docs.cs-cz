---
title: Přepisovatelné členské funkce CWinApp
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 28ba243bd755e25db5f2cb03d08013f082fbc918
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447262"
---
# <a name="overridable-cwinapp-member-functions"></a>Přepisovatelné členské funkce CWinApp

[CWinApp](../mfc/reference/cwinapp-class.md) poskytuje několik klíčových členských funkcí, které lze přepsat (`CWinApp` přepisuje tyto členy z třídy [CWinThread](../mfc/reference/cwinthread-class.md), ze které `CWinApp` odvozeny):

- [InitInstance](../mfc/initinstance-member-function.md)

- [Spouštěl](../mfc/run-member-function.md)

- [ExitInstance –](../mfc/exitinstance-member-function.md)

- [OnIdle –](../mfc/onidle-member-function.md)

Jediná `CWinApp` členská funkce, kterou je nutné přepsat, je `InitInstance`.

## <a name="see-also"></a>Viz také

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
