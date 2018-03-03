---
title: "Zajišťování aktivace bez oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb33f1dd9f8be8cb06cdfcc2aeecb653c2762410
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="providing-windowless-activation"></a>Zajišťování aktivace bez oken
Okno vytváření kódu (to znamená, vše, co se stane, když zavoláte **CreateWindow**) může být provést. Ovládací prvek, který udržuje obrazovce okno má ke správě zprávy pro okno. Bez oken ovládací prvky jsou proto rychlejší než ovládací prvky se systémem windows.  
  
 Další výhodou bez oken ovládací prvky je, že, na rozdíl od oddílové ovládacích prvků, bez oken ovládací prvky podporují transparentní Malování a oblasti nepravoúhlý obrazovky. Běžným příkladem ovládacího prvku transparentní je ovládacího prvku typu textový s průhledným pozadím. Ovládací prvky vybarví text, ale ne na pozadí, aby vše, co je pod text zobrazuje prostřednictvím. Novější formulářů často Ujistěte se, použijte nepravoúhlý ovládacích prvků, jako je například šipky a zaokrouhlit tlačítka.  
  
 Často ovládacího prvku nemusí své vlastní okno a místo toho můžete použít okno služby jeho kontejneru, za předpokladu, že kontejner byl zapsán do podporují objekty bez oken. Bez oken ovládací prvky jsou zpětně kompatibilní se starší kontejnery. Bez oken ovládací prvky v kontejnerech starší nezapíše se na podporu bez oken ovládací prvky, vytvoření okna při aktivní.  
  
 Protože bez oken ovládací prvky nemají své vlastní windows, kontejneru (která má okno) zodpovídá za poskytování služby, které by jinak byly zadány ovládacího prvku vlastní období. Například pokud ovládacího prvku potřebuje dotazovat fokus klávesnice, zachycení myši nebo získat kontext zařízení, tyto operace jsou spravovány kontejneru. Kontejner směruje uživatele vstupní zprávy odeslané do jeho okna do ovládacího prvku bez oken odpovídající pomocí `IOleInPlaceObjectWindowless` rozhraní. (Viz *ActiveX SDK* popis tohoto rozhraní.) `COleControl` členské funkce vyvolání tyto služby z kontejneru.  
  
 Chcete-li vlastní ovládací prvek použít aktivace bez oken, zahrnují **windowlessActivate** příznak v sadě příznaky vrácený [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Příklad:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]  
  
 Kód, který patří tento příznak vytváří automaticky, pokud jste vybrali **aktivace bez oken** možnost [nastavení řízení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránky Průvodce ovládacím prvkem ActiveX knihovny MFC.  
  
 Pokud je povolená aktivace bez oken, kontejneru budou delegovat to vstupní zprávy k ovládacímu prvku `IOleInPlaceObjectWindowless` rozhraní. `COleControl`je implementace tohoto rozhraní odešle zprávu zprávy prostřednictvím ovládacího prvku mapy zpráv, po úpravě myši koordinuje správně. Přidáním odpovídající položky do mapy zpráv může zpracovat zprávy jako obyčejnou okno zprávy. Ve vaší obslužné rutiny pro tyto zprávy, vyhněte se použití `m_hWnd` členské proměnné (nebo – členská funkce, která jej používá) bez první kontrola její hodnota není **NULL**.  
  
 `COleControl`Poskytuje členské funkce, které vyvolají zachycení myši, fokus klávesnice, posouvání a další okno služby z kontejneru podle potřeby, včetně:  
  
-   [Hodnotu GetFocus](../mfc/reference/colecontrol-class.md#getfocus), [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)  
  
-   [GetCapture](../mfc/reference/colecontrol-class.md#getcapture), [SetCapture](../mfc/reference/colecontrol-class.md#setcapture), [ReleaseCapture](../mfc/reference/colecontrol-class.md#releasecapture)  
  
-   [Getdc –](../mfc/reference/colecontrol-class.md#getdc), [ReleaseDC](../mfc/reference/colecontrol-class.md#releasedc)  
  
-   [InvalidateRgn](../mfc/reference/colecontrol-class.md#invalidatergn)  
  
-   [ScrollWindow](../mfc/reference/colecontrol-class.md#scrollwindow)  
  
-   [GetClientRect](../mfc/reference/colecontrol-class.md#getclientrect)  
  
 V ovládacích prvcích bez oken, byste měli vždycky používat `COleControl` členské funkce místo odpovídající `CWnd` členské funkce nebo jejich související funkce rozhraní API Win32.  
  
 Můžete bez oken ovládacího prvku jako cíl operace přetažení myší OLE. Za normálních okolností bude vyžadovat, aby ovládacího prvku okno být registrován jako cíle přetažení. Vzhledem k tomu, že ovládací prvek nemá žádné okno, kontejneru používá vlastní okno jako cíle přetažení. Poskytuje implementaci pro ovládací prvek `IDropTarget` rozhraní, ke kterému kontejneru můžete delegovat volání v příslušnou dobu. Pokud chcete vystavit toto rozhraní do kontejneru, přepište [COleControl::GetWindowlessDropTarget](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget). Příklad:  
  
 [!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md)

