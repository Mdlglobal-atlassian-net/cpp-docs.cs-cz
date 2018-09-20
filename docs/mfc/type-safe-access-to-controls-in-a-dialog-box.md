---
title: Typově bezpečný přístup k ovládacím prvkům v dialogovém okně | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- Windows common controls [MFC], in dialog boxes
- safe access to dialog box controls
- dialog boxes [MFC], type-safe access to controls
- controls [MFC], accessing in dialog boxes
- type-safe access to dialog box controls
- MFC dialog boxes [MFC], type-safe access to controls
ms.assetid: 67021025-dd93-4d6a-8bed-a1348fe50685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ed8a374c34eacc48e1d877e704fdc60a20f33d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422711"
---
# <a name="type-safe-access-to-controls-in-a-dialog-box"></a>Typově bezpečný přístup k ovládacím prvkům v dialogovém okně

Ovládací prvky v dialogovém okně mohou používat rozhraní tříd ovládacích prvků MFC jako `CListBox` a `CEdit`. Můžete vytvořit objekt ovládacího prvku a připojit ho k ovládacímu prvku dialogového okna. K tomuto ovládacímu prvku pak získáte přístup prostřednictvím rozhraní jeho třídy voláním členských funkcí ovládajících tento ovládací prvek. Zde popsané metody poskytují přístup k ovládacímu prvku se zajištěním bezpečnosti typů. To je zvláště užitečné pro ovládací prvky, jako jsou textová pole a pole se seznamem.

Existují dva přístupy k propojení mezi ovládacím prvkem v dialogovém okně a proměnnou člena ovládacího prvku C++ v `CDialog`-odvozené třídy:

- [Bez průvodců kódem](../mfc/type-safe-access-to-controls-without-code-wizards.md)

- [S použitím průvodců kódem](../mfc/type-safe-access-to-controls-with-code-wizards.md)

## <a name="see-also"></a>Viz také

[Dialogová okna](../mfc/dialog-boxes.md)

