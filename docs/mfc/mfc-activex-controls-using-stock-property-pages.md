---
title: 'MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb1f1d9eed313fefc04a14a004af8c35309949bf
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45534986"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností
Tento článek popisuje, k dispozici pro ovládací prvky ActiveX a způsob jejich použití stránek uložených vlastností.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).  
  
 Další informace o použití stránek vlastností v ovládacím prvku ActiveX najdete v následujících článcích:  
  
-   [MFC – ovládací prvky ActiveX: Stránky vlastností](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [MFC – ovládací prvky ActiveX: Přidání další stránky přizpůsobených vlastností](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
 Knihovna MFC poskytuje tři stránky uložených vlastností pro použití s ovládacími prvky ActiveX: `CLSID_CColorPropPage`, `CLSID_CFontPropPage`, a `CLSID_CPicturePropPage`. Tyto stránky zobrazují uživatelské rozhraní pro základní barvy, písma a vlastnosti obrázku, v uvedeném pořadí.  
  
 Zahrnout tyto stránky vlastností do ovládacího prvku, přidejte svoje ID kódu, který inicializuje ovládacího prvku pole ID stránek vlastností. V následujícím příkladu, tento kód umístěný v souboru implementace ovládacího prvku (. CPP), inicializuje pole tak, aby obsahovala všechny tři stránky uložených vlastností a výchozí stránky vlastností (s názvem `CMyPropPage` v tomto příkladu):  
  
 [!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]  
  
 Všimněte si, že počet stránek vlastností v BEGIN_PROPPAGEIDS – makro je 4. To představuje počet stránek vlastností podporuje ovládací prvek ActiveX.  
  
 Po provedení těchto změn znovu sestavte projekt. Ovládací prvek má teď stránek vlastností písma, obrázku a vlastností barev.  
  
> [!NOTE]
>  Pokud stránky uložených vlastností ovládacího prvku nelze získat přístup, může být vzhledem k tomu, že knihovna MFC DLL (MFCxx.DLL) nebyl registrován správně s aktuálním operačním systémem. Tato situace obvykle vzniká v instalaci Visual C++ v části operační systém jiný než ten, který aktuálně běží.  
  
> [!TIP]
>  Pokud vaše stránky uložených vlastností nejsou viditelné (viz předchozí poznámce), zaregistruje knihovnu DLL spuštěním RegSvr32.exe z příkazového řádku pomocí úplný název cesty k souboru DLL.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)   
 [MFC – ovládací prvky ActiveX: Přidání uložených vlastností](../mfc/mfc-activex-controls-adding-stock-properties.md)

