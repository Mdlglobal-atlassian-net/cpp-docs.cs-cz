---
title: 'MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností'
ms.date: 09/12/2018
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
helpviewer_keywords:
- picture stock property pages [MFC]
- CLSID_CFontPropPage [MFC]
- color stock property pages [MFC]
- CLSID_CColorPropPage [MFC]
- fonts [MFC], ActiveX controls
- stock properties [MFC], stock property pages
- CLSID_CPicturePropPage [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
ms.openlocfilehash: 13a0edb72657c9ffad00dcb909019bdfe4b87e11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358204"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností

Tento článek popisuje stránky vlastností zásob, které jsou k dispozici pro ovládací prvky ActiveX, a jejich použití.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

Další informace o použití stránek vlastností v ovládacím prvku ActiveX naleznete v následujících článcích:

- [MFC – ovládací prvky ActiveX: Stránky vlastností](../mfc/mfc-activex-controls-property-pages.md)

- [MFC – ovládací prvky ActiveX: Přidání další stránky přizpůsobených vlastností](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

Knihovna MFC poskytuje tři stránky vlastností `CLSID_CColorPropPage` `CLSID_CFontPropPage`zásob `CLSID_CPicturePropPage`pro použití s ovládacími prvky ActiveX: , a . Tyto stránky zobrazují uživatelské rozhraní pro základní barvy, písma a vlastnosti obrázku.

Chcete-li tyto stránky vlastností začlenit do ovládacího prvku, přidejte jejich ID do kódu, který inicializuje id stránky vlastností ovládacího prvku. V následujícím příkladu tento kód, který se nachází v souboru implementace ovládacího prvku (. CPP), inicializuje pole tak, aby obsahovalo všechny tři `CMyPropPage` stránky vlastností akcií a výchozí stránku vlastností (pojmenovanou v tomto příkladu):

[!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

Všimněte si, že počet stránek vlastností v makru BEGIN_PROPPAGEIDS je 4. To představuje počet stránek vlastností podporovaných ovládacím prvkem ActiveX.

Po provedené mši znovu vytvořte projekt. Ovládací prvek má nyní stránky vlastností pro vlastnosti písma, obrázku a barvy.

> [!NOTE]
> Pokud nelze získat přístup ke stránkám vlastností kontrolního skladu, může to být způsobeno tím, že knihovna MFC DLL (MFCxx.DLL) nebyla správně zaregistrována u aktuálního operačního systému. To obvykle vyplývá z instalace visual c++ v operačním systému, který se liší od aktuálně spuštěného operačního systému.

> [!TIP]
> Pokud vaše stránky vlastností stock nejsou viditelné (viz předchozí poznámka), zaregistrujte dll spuštěním RegSvr32.exe z příkazového řádku s úplným názvem cesty k dll.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Přidání uložených vlastností](../mfc/mfc-activex-controls-adding-stock-properties.md)
