---
title: 'Kontejnery ovládacích prvků ActiveX: Vložení ovládacího prvku do kontejnerové aplikace ovládacího prvku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f025c9fa564bcd37c585db6ea5c5cd0f5be83e0d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432136"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>ActiveX – kontejnery ovládacích prvků: Vložení ovládacího prvku do kontejnerové aplikace ovládacího prvku

Pro přístup k ovládacím prvku ActiveX z aplikace kontejneru ovládacího prvku ActiveX, musíte přidat ovládací prvek ActiveX do kontejneru pomocí aplikace [vložit ovládací prvek ActiveX](../windows/insert-activex-control-dialog-box.md) dialogové okno.

Přidání ovládacího prvku ActiveX k projektu kontejneru ovládacího prvku ActiveX naleznete v tématu [zobrazení a přidání ovládacích prvků ActiveX do dialogového okna](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

Jakmile přidáte ovládací prvek, musíte přidat členské proměnné (typ ovládacího prvku ActiveX) do třídy dialogového okna. Další informace o tomto postupu najdete v tématu [přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md).

Po přidání členské proměnné třídy, označuje jako obálkovou třídu, je automaticky generují a přidávají do vašeho projektu. Tato třída se používá jako rozhraní mezi kontejnerem ovládacího prvku a vloženému ovládacímu prvku.

## <a name="see-also"></a>Viz také

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

