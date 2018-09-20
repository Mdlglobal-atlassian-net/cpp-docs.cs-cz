---
title: Typově bezpečný přístup k ovládacím prvkům bez průvodců kódem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2685c946b9ee1c738ee83f9413b7fd955857febb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438337"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Typově bezpečný přístup k ovládacím prvkům bez průvodců kódem

První postup k vytvoření typově bezpečný přístup k ovládacím prvkům používá vložené členské funkce přetypovat návratový typ třídy `CWnd`společnosti `GetDlgItem` členskou funkci na příslušný typ ovládacího prvku jazyka C++, jako v následujícím příkladu:

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

Potom můžete tuto funkci člena pro přístup k ovládacímu prvku způsobem typově bezpečný kód podobný následujícímu:

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>Viz také

[Typově bezpečný přístup k ovládacím prvkům v dialogovém okně](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Typově bezpečný přístup k ovládacím prvkům s průvodci kódem](../mfc/type-safe-access-to-controls-with-code-wizards.md)

