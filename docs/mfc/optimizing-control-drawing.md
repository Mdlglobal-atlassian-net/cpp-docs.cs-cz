---
title: Optimalizace vykreslování ovládacích prvků
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
ms.openlocfilehash: 4d0037ebdfe56690be2f18a2790b2b13967e337c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274177"
---
# <a name="optimizing-control-drawing"></a>Optimalizace vykreslování ovládacích prvků

Když ovládací prvek je nastaven na vykreslit do kontextu zařízení zadaný kontejner, ho obvykle vybere objekty GDI (například pera, štětců a písma) do kontextu zařízení, provádí její kreslicí operace a obnoví předchozí objekty GDI. Pokud kontejner má více ovládacích prvků, které se mají vykreslit do stejného kontextu zařízení a každý ovládací prvek: výběr GDI objekty, které vyžaduje, pokud ovládací prvky neobnovujte jednotlivě dříve vybrané objekty se šetří čas. Po čerpali všechny ovládací prvky kontejneru můžete automaticky obnovit původní objekty.

Ke zjištění, zda kontejner podporuje tuto techniku, můžete volat ovládací prvek [COleControl::IsOptimizedDraw](../mfc/reference/colecontrol-class.md#isoptimizeddraw) členskou funkci. Pokud tato funkce vrací **TRUE**, ovládací prvek můžete přeskočit na normální krok obnovení dříve vybrané objekty.

Vezměte v úvahu ovládací prvek, který má následující (neoptimalizované) `OnDraw` funkce:

[!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/cpp/optimizing-control-drawing_1.cpp)]

Pero a štětce v tomto příkladu jsou lokální proměnné, což znamená jejich destruktory bude volána při mizení z rozsahu (když `OnDraw` funkce skončí). Destruktory se pokus o odstranění odpovídající objekty GDI. Ale se nesmí odstranit, pokud budete chtít nechat vybrali do kontextu zařízení při návratu z `OnDraw`.

Aby se zabránilo [cpen –](../mfc/reference/cpen-class.md) a [cbrush –](../mfc/reference/cbrush-class.md) objekty z při rušení `OnDraw` dokončí, uložit je do proměnné členů místo místních proměnných. V deklaraci třídy ovládacího prvku přidejte deklarace pro dvě nové členské proměnné:

[!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/cpp/optimizing-control-drawing_2.h)]
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/cpp/optimizing-control-drawing_3.h)]

Pak, bude `OnDraw` funkce může být přepsán následujícím způsobem:

[!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/cpp/optimizing-control-drawing_4.cpp)]

Tento přístup se vyhnete vytvoření pera a štětce pokaždé, když `OnDraw` je volána. Vylepšení rychlosti dodává za cenu udržování dat další instanci.

Pokud se změní vlastnost ForeColor nebo BackColor pera nebo štětce musí být znovu vytvořen. Chcete-li to provést, přepište [OnForeColorChanged](../mfc/reference/colecontrol-class.md#onforecolorchanged) a [OnBackColorChanged](../mfc/reference/colecontrol-class.md#onbackcolorchanged) členské funkce:

[!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/cpp/optimizing-control-drawing_5.cpp)]

Nakonec eliminovat zbytečné `SelectObject` volání, upravte `OnDraw` následujícím způsobem:

[!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/cpp/optimizing-control-drawing_6.cpp)]

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md)<br/>
[COleControl – třída](../mfc/reference/colecontrol-class.md)<br/>
[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[Průvodce ovládacím prvkem ActiveX v prostředí MFC](../mfc/reference/mfc-activex-control-wizard.md)<br/>
[MFC – ovládací prvky ActiveX: Vykreslování ovládacího prvku ActiveX](../mfc/mfc-activex-controls-painting-an-activex-control.md)
