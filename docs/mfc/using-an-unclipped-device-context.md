---
title: "Použití Neoříznutého kontextu zařízení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ae095b59b07132bd7e4c6892b8e58d9e69fb39c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-unclipped-device-context"></a>Použití neoříznutého kontextu zařízení
Pokud jste si naprosto jisti, že vlastní ovládací prvek není malovat mimo jeho obdélníku klienta, můžete zaznamenat nárůst malé ale rozpoznat rychlost zakázáním volání `IntersectClipRect` , je provedené `COleControl`. Chcete-li to provést, odeberte **clipPaintDC** příznak ze sady příznaky vrácený [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Příklad:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]  
  
 Kód, který chcete odebrat tento příznak vytváří automaticky, pokud jste vybrali **Neoříznutého kontextu zařízení** možnost [nastavení řízení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránky, při vytváření vlastního ovládacího prvku pomocí Průvodce ovládacím prvkem ActiveX knihovny MFC.  
  
 Pokud používáte aktivace bez oken, optimalizace nemá žádný vliv.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md)

