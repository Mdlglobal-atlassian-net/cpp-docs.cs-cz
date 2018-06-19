---
title: Optimalizace vykreslování ovládacích prvků | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8103e1e342756f9b715c1a0959ed256403e130bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351291"
---
# <a name="optimizing-control-drawing"></a>Optimalizace vykreslování ovládacích prvků
Při ovládacího prvku je odeslán pokyn k vykreslení sám v kontextu zadaný kontejner zařízení, je obvykle vybere objekty GDI (například pera, štětce a písem) do kontextu zařízení, provede jeho kreslení operací a obnoví předchozí objekty GDI. Pokud kontejneru má více ovládacích prvků, které mají být vykresleny do stejného kontextu zařízení a každý ovládací prvek vybere GDI objekty, které vyžaduje, čas může být uloženy ovládací prvky neobnovujte jednotlivě dříve vybrané objekty. Po čerpají všechny ovládací prvky kontejneru automaticky obnovit původní objekty.  
  
 Chcete-li zjistit, zda kontejner podporuje tato technika, ovládacího prvku zavolat [COleControl::IsOptimizedDraw](../mfc/reference/colecontrol-class.md#isoptimizeddraw) – členská funkce. Pokud funkce vrátí hodnotu **TRUE**, ovládacího prvku můžete přeskočit normální krok obnovení dříve vybrané objekty.  
  
 Vezměte v úvahu ovládací prvek, který má následující (neoptimalizované) `OnDraw` funkce:  
  
 [!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/cpp/optimizing-control-drawing_1.cpp)]  
  
 Pera a štětce v tomto příkladu jsou místní proměnné, tj. jejich destruktory bude volána, když se dostala mimo rozsah (Pokud `OnDraw` funkce elementy end). Destruktorech se pokusí odstranit odpovídající objekty GDI. Ale jejich by neměl být odstraněn v případě, že máte v plánu je vybrané do kontextu zařízení při vrácení z ponechte `OnDraw`.  
  
 Aby se zabránilo [CPen](../mfc/reference/cpen-class.md) a [CBrush](../mfc/reference/cbrush-class.md) objekty z zničen při `OnDraw` skončí, uložit je do proměnné členů místo lokální proměnné. V deklaraci třídy ovládacího prvku přidejte deklarace pro dvě nové proměnné člena:  
  
 [!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/cpp/optimizing-control-drawing_2.h)]  
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/cpp/optimizing-control-drawing_3.h)]  
  
 Potom, `OnDraw` funkce může být přepsán následujícím způsobem:  
  
 [!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/cpp/optimizing-control-drawing_4.cpp)]  
  
 Tento přístup zabraňuje vytvoření pera a štětce pokaždé, když `OnDraw` je volána. Rychlost zlepšování dodává cenu údržbu dat další instanci.  
  
 Pokud vlastnost ForeColor nebo BackColor změní, pera nebo štětce musí být znovu vytvořen. Chcete-li to provést, přepište [OnForeColorChanged](../mfc/reference/colecontrol-class.md#onforecolorchanged) a [OnBackColorChanged](../mfc/reference/colecontrol-class.md#onbackcolorchanged) členské funkce:  
  
 [!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/cpp/optimizing-control-drawing_5.cpp)]  
  
 Nakonec k vyloučení nepotřebných `SelectObject` volání, upravte `OnDraw` následujícím způsobem:  
  
 [!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/cpp/optimizing-control-drawing_6.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX: optimalizace](../mfc/mfc-activex-controls-optimization.md)   
 [COleControl – třída](../mfc/reference/colecontrol-class.md)   
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [Průvodce ovládacím prvkem ActiveX knihovny MFC](../mfc/reference/mfc-activex-control-wizard.md)   
 [MFC – ovládací prvky ActiveX: Vykreslování ovládacího prvku ActiveX](../mfc/mfc-activex-controls-painting-an-activex-control.md)

