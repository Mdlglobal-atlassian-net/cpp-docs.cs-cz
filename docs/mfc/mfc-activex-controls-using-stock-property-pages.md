---
title: "Ovládací prvky MFC ActiveX: Použití stránek uložených vlastností | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 04f49395959ec3b62f20716ddfb4ba7f4d89032d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností
Tento článek popisuje dostupné pro ovládací prvky ActiveX a jejich použití stránek uložených vlastností.  
  
 Další informace o použití stránek vlastností v ovládacím prvku ActiveX najdete v následujících článcích:  
  
-   [Ovládací prvky MFC ActiveX: Stránky vlastností](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [Ovládací prvky MFC ActiveX: Přidání další stránky přizpůsobených vlastností](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
 MFC poskytuje tři stránky uložených vlastností pro použití s ovládacími prvky ActiveX: **CLSID_CColorPropPage**, **CLSID_CFontPropPage**, a **CLSID_CPicturePropPage**. Tyto stránek zobrazit uživatelské rozhraní pro uložené barvy, písma a vlastnosti obrázku, v uvedeném pořadí.  
  
 Do ovládacího prvku zahrnout tyto stránek vlastností, přidejte jejich ID na kód, který inicializuje ovládacího prvku pole stránky vlastnost ID. V následujícím příkladu, tento kód nachází v souboru implementaci ovládacího prvku (. CPP), inicializuje pole tak, aby obsahovala všechny tři stránky uložených vlastností a stránky vlastností výchozí (s názvem `CMyPropPage` v tomto příkladu):  
  
 [!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]  
  
 Všimněte si, že počet vlastností v stránky `BEGIN_PROPPAGEIDS` makro, je 4. To představuje číslo stránky vlastností nepodporuje ovládací prvek ActiveX.  
  
 Poté, co byly provedeny změny, znovu sestavte projekt. Stránky vlastností pro písma, obrázku a vlastností barev teď má vlastní ovládací prvek.  
  
> [!NOTE]
>  Pokud stránky uložených vlastností ovládacího prvku nelze získat přístup, může být protože MFC DLL (MFCxx.DLL) nebyl správně zaregistrován v aktuálním operačním systému. Tato situace obvykle vzniká v instalaci Visual C++ v části liší od aktuálně spuštěné verze operačního systému.  
  
> [!TIP]
>  Pokud vaše stránky uložených vlastností nejsou viditelné (viz předchozí poznámce) a zaregistruje knihovnu DLL tak, že spustíte RegSvr32.exe z příkazového řádku s úplnou cestu k souboru DLL.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [Ovládací prvky MFC ActiveX: Přidání uložených vlastností](../mfc/mfc-activex-controls-adding-stock-properties.md)
