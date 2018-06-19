---
title: 'Postupy: přizpůsobení tlačítka aplikace | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 828886e6a5c4891e1fd7e1d820ee00542e052cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351361"
---
# <a name="how-to-customize-the-application-button"></a>Postupy: Přizpůsobení tlačítka aplikace
Když kliknete na tlačítko aplikace, zobrazí se nabídka příkazů. Obvykle se v nabídce obsahuje příkazů týkajících se souboru, jako **otevřete**, **Uložit**, **tiskových**, a **ukončení**.  
  
 ![Tlačítko aplikace pásu karet MFC](../mfc/media/application_button.png "application_button")  
  
 Chcete-li přizpůsobení tlačítka aplikace, otevřete ho v **vlastnosti** okně upravit její vlastnosti a poté zobrazte náhled ovládacího prvku pásu karet.  
  
### <a name="to-open-the-application-button-in-the-properties-window"></a>Otevřete v okně vlastností tlačítka aplikace  
  
1.  V sadě Visual Studio na **zobrazení** nabídky, klikněte na tlačítko **zobrazení prostředků**.  
  
2.  V **zobrazení prostředků**, dvakrát klikněte na prostředek pásu karet, která se zobrazí na návrhovou plochu.  
  
3.  Na návrhové ploše, klikněte pravým tlačítkem na nabídku tlačítko aplikace a pak klikněte na **vlastnosti**.  
  
## <a name="application-button-properties"></a>Vlastnosti tlačítka aplikace  
 Následující tabulka definuje vlastnosti tlačítka aplikace.  
  
|Vlastnost|Definice|  
|--------------|----------------|  
|**Tlačítka**|Obsahuje kolekci až tři tlačítka, které se zobrazují v pravém dolním rohu na nabídku aplikace.|  
|**Popisek**|Určuje text ovládacího prvku. Na rozdíl od dalších prvků pásu karet tlačítko aplikace nejsou zobrazeny text titulku. Místo toho text se používá pro usnadnění přístupu.|  
|**Obrázek HDPI**|Určuje identifikátor vysoké bodů na palec ikona tlačítko (HDPI) aplikace. Při spuštění aplikace na vysokou DPI monitorování, **HDPI Image** se používá místo **Image**.|  
|**HDPI velkých obrázků**|Určuje identifikátor vysoké DPI velkých obrázků. Pokud aplikace běží na monitorování vysoké DPI **velkých obrázků HDPI** se používá místo **velkých obrázků**.|  
|**HDPI malých obrázků**|Určuje identifikátor vysoké DPI malých obrázků. Při spuštění aplikace na vysokou DPI monitorování, **malých obrázků HDPI** se používá místo **malých obrázků**.|  
|**ID**|Určuje identifikátor ovládacího prvku.|  
|**Obrázek**|Určuje identifikátor tlačítko ikona aplikace. Ikona je 26 x 26 32-bit rastrového obrázku, který má průhlednost alfa. Průhledné plochy na ikonu se zvýrazněnou při kliknutí na nebo při přechodu myší nad tlačítka aplikace.|  
|**Klíče**|Určuje řetězec, který se zobrazí, když je povolena klíč tip navigace. Navigační tlačítka klíč je povoleno po stisknutí klávesy ALT.|  
|**Velkých obrázků**|Určuje identifikátor bitové kopie, který obsahuje řadu ikony 32 x 32. Ikony jsou používány tlačítka v kolekci hlavní položky.|  
|**Hlavní položky**|Obsahuje kolekci položek nabídky, které se zobrazují v nabídce aplikace.|  
|**Popisek naposledy použitých**|Určuje text zobrazený na seznam posledních panelu.|  
|**Malé bitové kopie**|Určuje identifikátor bitové kopie, který obsahuje řadu ikony velikosti 16 x 16. Ikony jsou používány tlačítka v kolekci tlačítka.|  
|**Použití**|Povolí nebo zakáže na seznam posledních panelu. Seznam naposledy použitých panelu se zobrazí v nabídce aplikace.|  
|**Šířka**|Určuje šířku v pixelech seznam naposledy použitých panelu.|  
  
 V nabídce aplikace se nezobrazí na návrhovou plochu. K jejímu zobrazení, musíte zobrazit náhled na pásu karet nebo spuštění aplikace.  
  
#### <a name="to-preview-the-ribbon-control"></a>Zobrazte náhled ovládacího prvku pásu karet  
  
-   Na **panelu nástrojů editoru pásu karet**, klikněte na **testovací pásu karet**.  
  
## <a name="see-also"></a>Viz také  
 [Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)

