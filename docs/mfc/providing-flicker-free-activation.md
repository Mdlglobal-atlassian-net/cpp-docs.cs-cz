---
title: "Zajištění aktivace bez blikání | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f98cc77ecc11f2b3ea07352e48c1e6a096125300
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="providing-flicker-free-activation"></a>Zajištění aktivace bez blikání
Pokud vlastní ovládací prvek nevykresluje samotné stejně jako ve stavu neaktivní a aktivní (a nepoužívá aktivace bez oken), můžete eliminovat kreslení operace a doprovodné visual blikání, které obvykle dojít při provádění přechod mezi neaktivní a aktivní stavy. Chcete-li to provést, zahrňte **noFlickerActivate** příznak v sadě příznaky vrácený [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Příklad:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]  
  
 Kód, který patří tento příznak vytváří automaticky, pokud jste vybrali **aktivace bez blikání** možnost [nastavení řízení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránka při vytváření vlastního ovládacího prvku pomocí Průvodce ovládacím prvkem ActiveX knihovny MFC.  
  
 Pokud používáte aktivace bez oken, optimalizace nemá žádný vliv.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX: optimalizace](../mfc/mfc-activex-controls-optimization.md)

