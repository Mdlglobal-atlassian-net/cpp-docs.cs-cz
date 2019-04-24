---
title: Zajištění interakce s myší v neaktivním stavu
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
ms.openlocfilehash: d37deeec06551ae8bf340c99a9759327ce2ec2b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297122"
---
# <a name="providing-mouse-interaction-while-inactive"></a>Zajištění interakce s myší v neaktivním stavu

Pokud váš ovládací prvek není aktivovat hned, stále můžete se k procesu ovládací prvky WM_SETCURSOR a wm_mousemove a zprávy, i v případě, že ovládací prvek nemá žádné okno. Můžete to provést povolením `COleControl`provádění `IPointerInactive` rozhraní, které je ve výchozím nastavení zakázané. (Viz *ActiveX SDK* popis tohoto rozhraní.) Ho Pokud chcete povolit, zahrňte příznak pointerInactive v sadě příznaky vrácený [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags):

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]

Kód, který patří tento příznak není automaticky vygenerován, pokud vyberete **myši ukazatel oznámení při neaktivní** možnost [nastavení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránce při vytváření ovládacího prvku s **Průvodce ovládacím prvkem ActiveX knihovny MFC**.

Když `IPointerInactive` rozhraní je povoleno, kontejner deleguje ovládací prvky WM_SETCURSOR a wm_mousemove a zprávy do něj. `COleControl`pro implementaci `IPointerInactive` odesílá zprávy přes mapu zpráv ovládacího prvku po nastavení myši koordinuje odpovídajícím způsobem. Zprávy stejně jako běžné okno zprávy může zpracovat tak, že přidáte odpovídající položky v mapování zprávy. V obslužné rutině pro tyto zprávy, vyhněte se použití *m_hWnd* členské proměnné (nebo žádnou členskou funkci, která ji používá) bez nejdřív zkontrolovali, že její hodnota není **NULL**.

Můžete také neaktivní ovládací prvek jako cíl operace přetažení myší OLE. Tento postup vyžaduje aktivaci ovládacího prvku v tuto chvíli uživatel přetáhne objekt přes něj, tak, aby okno ovládacího prvku lze zaregistrovat jako cíl přetažení. Způsobí aktivace během přetáhněte přepsat [COleControl::GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)a vrátí příznak POINTERINACTIVE_ACTIVATEONDRAG:

[!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]

Povolení `IPointerInactive` rozhraní obvykle znamená, že ovládací prvek dokáže zpracovávat zprávy týkající se myši za všech okolností. Chcete-li získat toto chování v kontejneru, který nepodporuje `IPointerInactive` rozhraní, musíte mít ovládací prvek vždy aktivována, když je viditelné, to znamená, že ovládací prvek by měl obsahovat příznak OLEMISC_ACTIVATEWHENVISIBLE mezi jeho různé příznaky. Ale, aby se zabránilo tento příznak z neprojeví v kontejneru, který podporuje `IPointerInactive`, můžete také zadat příznak OLEMISC_IGNOREACTIVATEWHENVISIBLE:

[!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md)
