---
title: Zajištění interakce s myší v neaktivním stavu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c322493a0ee1aebd068ffe1fedb695445b6274aa
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929491"
---
# <a name="providing-mouse-interaction-while-inactive"></a>Zajištění interakce s myší v neaktivním stavu
Pokud vlastní ovládací prvek není aktivovat hned, stále můžete ho do procesu WM_SETCURSOR a WM_MOUSEMOVE zprávy, i když ovládací prvek nemá žádné okno. To lze provést povolením `COleControl`na implementaci `IPointerInactive` rozhraní, které se ve výchozím nastavení vypnutá. (Viz *ActiveX SDK* popis tohoto rozhraní.) Ho Pokud chcete zapnout, zahrnout příznak pointerInactive sadu příznaky vrácený [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags):  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]  
  
 Kód, který patří tento příznak vytváří automaticky, pokud jste vybrali **myši ukazatel oznámení při neaktivní** možnost [nastavení řízení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránka při vytváření vlastního ovládacího prvku pomocí **Průvodce ovládacím prvkem ActiveX knihovny MFC**.  
  
 Když `IPointerInactive` rozhraní je povoleno, kontejneru deleguje WM_SETCURSOR a WM_MOUSEMOVE zprávy do něj. `COleControl`pro implementaci `IPointerInactive` expeduje zprávy prostřednictvím ovládacího prvku mapy zpráv, po úpravě myši koordinuje správně. Přidáním odpovídající položky do mapy zpráv může zpracovat zprávy stejně jako obyčejnou okno zprávy. Ve vaší obslužné rutiny pro tyto zprávy, vyhněte se použití *m_hWnd* členské proměnné (nebo – členská funkce, která jej používá) bez první kontrola její hodnota není **NULL**.  
  
 Můžete také ovládací prvek neaktivní jako cíl operace přetažení myší OLE. To vyžaduje aktivaci ovládacího prvku v okamžiku, kdy uživatel nastavuje tažením objekt přes, tak, aby ovládacího prvku okno může být registrován jako cíle přetažení. Aby aktivace proběhnout během přetažení, přepsání [COleControl::GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)a vrátí příznak POINTERINACTIVE_ACTIVATEONDRAG:  
  
 [!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]  
  
 Povolení `IPointerInactive` rozhraní obvykle znamená, že chcete být schopná zpracovávat myši zpráv za všech okolností ovládacího prvku. Chcete-li získat toto chování v kontejneru, který nepodporuje `IPointerInactive` rozhraní, musíte mít kontrolu nad vždy aktivovat, pokud viditelná, což znamená, že ovládacího prvku by měla obsahovat příznak OLEMISC_ACTIVATEWHENVISIBLE mezi její různé příznaky. Ale, aby se zabránilo tento příznak z trvá vliv v kontejneru, který podporuje `IPointerInactive`, můžete také zadat příznak OLEMISC_IGNOREACTIVATEWHENVISIBLE:  
  
 [!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md)

