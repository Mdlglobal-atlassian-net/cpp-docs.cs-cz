---
title: Práce s objekty oken
ms.date: 11/04/2016
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
ms.openlocfilehash: c696d880ffa69b0a0399c5282621546c5783ebe4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399483"
---
# <a name="working-with-window-objects"></a>Práce s objekty oken

Práce s volání systému windows pro dva typy aktivit:

- Zpracování zpráv Windows

- Kreslení v okně

Zpracování zpráv s Windows v jakékoli okno, včetně vlastních podřízených oken, naleznete v tématu [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md) k mapování zpráv na třídě okna C++. Zapište obslužná rutina zprávy členské funkce ve své třídě.

Většina kreslení v rozhraní framework aplikace vyvolá se v zobrazení, jejichž [OnDraw](../mfc/reference/cview-class.md#ondraw) členská funkce je volána pokaždé, když je nutné vykreslit obsah okna. Pokud je vaše okno podřízené zobrazení, které může delegovat některé kreslení v zobrazení na podřízené okno tak, že `OnDraw` volání jednoho z vašich okno členské funkce.

V každém případě budete potřebovat kontext zařízení pro kreslení. Můžete použít základní pera, štětce a jiných grafických objektů obsažených v kontextu zařízení spojené s okno. Nebo můžete změnit tyto objekty vykreslování efektů, které potřebujete získat. S kontext zařízení můžete nastavit, volat členské funkce třídy [CDC](../mfc/reference/cdc-class.md) (třída podle kontextu zařízení) k vykreslení čar, tvary a text, použití barev; a pro práci s souřadnicový systém.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)

- [Kreslení v zobrazení](../mfc/drawing-in-a-view.md)

- [Kontexty zařízení](../mfc/device-contexts.md)

- [Grafické objekty](../mfc/graphic-objects.md)

## <a name="see-also"></a>Viz také:

[Objekty oken](../mfc/window-objects.md)
