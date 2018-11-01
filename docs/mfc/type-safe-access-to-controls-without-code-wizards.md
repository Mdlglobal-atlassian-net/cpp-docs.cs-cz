---
title: Typově bezpečný přístup k ovládacím prvkům bez průvodců kódem
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
ms.openlocfilehash: 2b337aa28d5fdf061d1db4b5cf66303688ef5bf3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501709"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Typově bezpečný přístup k ovládacím prvkům bez průvodců kódem

První postup k vytvoření typově bezpečný přístup k ovládacím prvkům používá vložené členské funkce přetypovat návratový typ třídy `CWnd`společnosti `GetDlgItem` členskou funkci na příslušný typ ovládacího prvku jazyka C++, jako v následujícím příkladu:

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

Potom můžete tuto funkci člena pro přístup k ovládacímu prvku způsobem typově bezpečný kód podobný následujícímu:

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>Viz také

[Typově bezpečný přístup k ovládacím prvkům v dialogovém okně](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Typově bezpečný přístup k ovládacím prvkům s průvodci kódem](../mfc/type-safe-access-to-controls-with-code-wizards.md)

