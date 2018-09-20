---
title: Zajišťování aktivace bez oken | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e8fc079921b3f2eddd117f93ee9d2f6cad60925
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441223"
---
# <a name="providing-windowless-activation"></a>Zajišťování aktivace bez oken

Kód pro vytvoření okna (to znamená, že vše, co se stane, když voláte `CreateWindow`) může být ke spuštění. Ovládací prvek, který udržuje na obrazovce má okno pro zprávy časového intervalu pro správu. Ovládací prvky bez oken, proto jsou rychlejší než ovládací prvky systému windows.

Další výhodou ovládací prvky bez oken je, že na rozdíl od oddílové ovládacích prvků, ovládací prvky bez oken podporují transparentní Malování a oblasti neobdélníkových obrazovky. Běžným příkladem transparentní ovládacího prvku je text ovládacího prvku s průhledným pozadím. Ovládací prvky jsou vykreslovány text, ale ne na pozadí, takže všechno, co je v části text zobrazí prostřednictvím. Novější formulářů často musíte dělat pomocí neobdélníkových prvků, třeba šipky a zaokrouhlit tlačítka.

Často ovládací prvek není nutné vlastní okna a místo toho můžete použít služby okna ze svého kontejneru, za předpokladu, že kontejner byl zapsán do podporují objekty bez oken. Ovládací prvky bez oken jsou zpětně kompatibilní s starší kontejnery. Ovládací prvky bez oken v kontejnerech starší nezapíše se do podporují ovládací prvky bez oken, vytvořit okno, pokud je aktivní.

Ovládací prvky bez oken nemají své vlastní windows, zodpovídá za poskytování služeb, které by jinak byly zadány pomocí okna ovládacího prvku vlastní kontejner (který má okno). Například pokud váš ovládací prvek potřebuje dotazovat fokus klávesnice, zachycení myši nebo získat kontext zařízení, tyto operace jsou spravovány kontejneru. Kontejner směruje uživatele vstupní zprávy odeslané do jeho okna na odpovídající ovládací prvek bez oken, pomocí `IOleInPlaceObjectWindowless` rozhraní. (Viz *ActiveX SDK* popis tohoto rozhraní.) `COleControl` členské funkce vyvolají tyto služby z kontejneru.

Chcete-li použít aktivace bez oken ovládacího prvku, patří **windowlessActivate** příznak v sadě příznaky vrácený [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Příklad:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]

Kód, který patří tento příznak není automaticky vygenerován, pokud vyberete **aktivace bez oken** možnost [nastavení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránky průvodce ovládací prvek ActiveX knihovny MFC.

Pokud je povolená aktivace bez oken, kontejner delegují vstupní zprávy do ovládacího prvku `IOleInPlaceObjectWindowless` rozhraní. `COleControl`pro implementaci tohoto rozhraní odesílá zprávy přes mapu zpráv ovládacího prvku, po nastavení myši koordinuje odpovídajícím způsobem. Zprávy jako běžný okno zprávy může zpracovat tak, že přidáte odpovídající položky v mapování zprávy. V obslužné rutině pro tyto zprávy, vyhněte se použití *m_hWnd* členské proměnné (nebo žádnou členskou funkci, která ji používá) bez nejdřív zkontrolovali, že její hodnota není **NULL**.

`COleControl` Poskytuje členské funkce, které vyvolají zachycení myši, fokus klávesnice, posouvání a jiné služby okna ze kontejneru podle potřeby, včetně:

- [Hodnotu GetFocus](../mfc/reference/colecontrol-class.md#getfocus), [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)

- [GetCapture](../mfc/reference/colecontrol-class.md#getcapture), [SetCapture](../mfc/reference/colecontrol-class.md#setcapture), [ReleaseCapture](../mfc/reference/colecontrol-class.md#releasecapture)

- [GetDC](../mfc/reference/colecontrol-class.md#getdc), [ReleaseDC](../mfc/reference/colecontrol-class.md#releasedc)

- [InvalidateRgn](../mfc/reference/colecontrol-class.md#invalidatergn)

- [ScrollWindow](../mfc/reference/colecontrol-class.md#scrollwindow)

- [GetClientRect](../mfc/reference/colecontrol-class.md#getclientrect)

V ovládací prvky bez oken, byste měli vždy používat `COleControl` členské funkce místo odpovídající `CWnd` členských funkcí nebo jejich související funkce rozhraní Win32 API.

Můžete chtít ovládací prvek bez oken cíl operace přetažení myší OLE. Za normálních okolností bude vyžadovat, že okno ovládacího prvku zaregistrovat jako cíl přetažení. Vzhledem k tomu, že ovládací prvek nemá žádná vlastní okna, kontejner používá vlastní okna jako cíl přetažení. Poskytuje implementaci ovládacího prvku `IDropTarget` rozhraní, ke které kontejner může delegovat volání v příslušnou dobu. Pokud chcete vystavit toto rozhraní do kontejneru, přepište [COleControl::GetWindowlessDropTarget](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget). Příklad:

[!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md)

