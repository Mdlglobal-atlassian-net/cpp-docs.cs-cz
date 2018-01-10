---
title: "Kontejnery ovládacích prvků ActiveX: Vložení ovládacího prvku do kontejnerové aplikace ovládacího prvku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a1eaaf0426726f252fc4990f06faa73b0598cfbb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>ActiveX – kontejnery ovládacích prvků: Vložení ovládacího prvku do kontejnerové aplikace ovládacího prvku
Než se dostanete z aplikací kontejneru ovládacího prvku ActiveX k ovládacího prvku ActiveX, musíte přidat ovládací prvek ActiveX do kontejneru aplikace pomocí [vložit ovládací prvek ActiveX](../windows/insert-activex-control-dialog-box.md) dialogové okno.  
  
 Přidání ovládacího prvku ActiveX do projektu kontejneru ovládacího prvku ActiveX naleznete v tématu [zobrazení a přidání ovládacích prvků ActiveX do dialogového okna](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 Jakmile přidáte ovládací prvek, je nutné přidat do třídy dialogového okna členské proměnné (of typ ovládacího prvku ActiveX). Další informace o tomto postupu najdete v tématu [přidání člena proměnné](../ide/adding-a-member-variable-visual-cpp.md).  
  
 Po přidání členské proměnné třídu, označuje jako obálkovou třídu, je automaticky generují a přidávají do projektu. Tato třída se používá jako rozhraní mezi kontejneru ovládacího prvku a vloženému ovládacímu prvku.  
  
## <a name="see-also"></a>Viz také  
 [ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

