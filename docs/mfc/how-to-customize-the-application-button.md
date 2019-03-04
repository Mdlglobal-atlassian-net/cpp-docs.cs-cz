---
title: 'Postupy: Přizpůsobení tlačítka aplikace'
ms.date: 11/19/2018
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
ms.openlocfilehash: d45ceaf1cce21f77871e966e0e8f525f95cb4c37
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269529"
---
# <a name="how-to-customize-the-application-button"></a>Postupy: Přizpůsobení tlačítka aplikace

Po kliknutí na tlačítko aplikace, zobrazí se nabídka příkazy. Obvykle se nabídka obsahuje příkazy, vztahující se k souboru, jako **otevřít**, **Uložit**, **tisk**, a **ukončovací**.

![Tlačítko aplikace pásu karet MFC](../mfc/media/application_button.png "tlačítko pásu karet aplikace knihovny MFC")

Chcete-li přizpůsobení tlačítka aplikace, otevřete ho v **vlastnosti** okně upravit její vlastnosti a pak zobrazte náhled ovládacího prvku pásu karet.

### <a name="to-open-the-application-button-in-the-properties-window"></a>Chcete-li otevřít tlačítko aplikace v okně Vlastnosti

1. V sadě Visual Studio na **zobrazení** nabídky, klikněte na tlačítko **zobrazení prostředků**.

1. V **zobrazení prostředků**, dvakrát klikněte na prostředek pásu karet se zobrazí na návrhové ploše.

1. Na návrhové ploše, klikněte pravým tlačítkem na tlačítko nabídky aplikace a pak klikněte na tlačítko **vlastnosti**.

## <a name="application-button-properties"></a>Vlastnosti tlačítka aplikace

Následující tabulka definuje vlastnosti tlačítko aplikace.

|Vlastnost|Definice|
|--------------|----------------|
|**Tlačítka**|Obsahuje kolekci až tři tlačítka, které se zobrazují v pravém dolním rohu nabídky aplikace.|
|**Titulek**|Určuje text ovládacího prvku. Na rozdíl od jiných prvků pásu karet tlačítku aplikace nejsou zobrazeny text titulku. Místo toho text slouží pro usnadnění přístupu.|
|**HDPI Image**|Určuje identifikátor vysokou bodů na palec ikona tlačítka (HDPI) aplikace. Při spuštění aplikace na vysoké rozlišení DPI monitoru, **HDPI Image** se použije namísto **Image**.|
|**HDPI Large Images**|Určuje identifikátor vysoké rozlišení DPI velké obrázky. Při spuštění aplikace na vysoké rozlišení DPI monitoru, **HDPI Large Images** se použije namísto **Large Images**.|
|**HDPI Small Images**|Určuje identifikátor vysoké rozlišení DPI malé obrázky. Při spuštění aplikace na vysoké rozlišení DPI monitoru, **HDPI Small Images** se použije namísto **Small Images**.|
|**ID**|Určuje identifikátor ovládacího prvku.|
|**Obrázek**|Určuje identifikátor ikonu pro tlačítko aplikace. Ikona je 26 × 26 32-bit rastrového obrázku, který má alfa průhlednosti. Transparentní části ikony jsou zvýrazněny při kliknutí nebo přechodu myši nad tlačítko aplikace.|
|**klíče**|Určuje řetězec, který se zobrazí při povolené navigaci pomocí popisu klávesy. Po stisknutí klávesy ALT je povolené navigaci pomocí popisu klávesy.|
|**Large Images**|Určuje identifikátor používaného obrázku, který obsahuje řadu ikony 32 x 32. Ikony jsou používány tlačítka v kolekci Main Items.|
|**Main Items**|Obsahuje kolekci položek nabídky, které se zobrazují v nabídce aplikace.|
|**Titulek naposledy použitých**|Určuje text zobrazený na seznam posledních panelu.|
|**Malé obrázky**|Určuje identifikátor používaného obrázku, který obsahuje řadu ikony 16 x 16. Ikony jsou používány tlačítka v kolekci tlačítek.|
|**Použití**|Povolí nebo zakáže na seznam posledních panelu. Seznam posledních panelu se zobrazí v nabídce aplikace.|
|**Šířka**|Určuje šířku v pixelech na seznam posledních panelu.|

Na nabídku aplikace se nezobrazí na návrhové ploše. Zobrazit, musíte zobrazit náhled pásu karet nebo spusťte aplikaci.

#### <a name="to-preview-the-ribbon-control"></a>Na pásu karet ovládací prvek náhledu

- Na **nástrojů editoru pásu karet**, klikněte na tlačítko **testovat pás karet**.

## <a name="see-also"></a>Viz také:

[Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)
