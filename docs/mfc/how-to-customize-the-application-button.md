---
title: 'Postupy: Tlačítko pro přizpůsobení aplikace'
ms.date: 09/07/2019
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
ms.openlocfilehash: 3a1d1625e80e6c6f4440864629a5123bed5744c7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907794"
---
# <a name="how-to-customize-the-application-button"></a>Postupy: Tlačítko pro přizpůsobení aplikace

Když kliknete na tlačítko aplikace, zobrazí se nabídka příkazů. Nabídka obvykle obsahuje příkazy týkající se souborů, jako je například **otevření**, **uložení**, **Tisk**a **ukončení**.

![Tlačítko aplikace pásu karet MFC](../mfc/media/application_button.png "Tlačítko aplikace pásu karet MFC")

Chcete-li přizpůsobit tlačítko aplikace, otevřete ho v okně **vlastnosti** (v **prostředky**), upravte jeho vlastnosti a potom zobrazte náhled ovládacího prvku pásu karet.

### <a name="to-open-the-application-button-in-the-properties-window"></a>Chcete-li otevřít tlačítko aplikace v okno Vlastnosti

1. V aplikaci Visual Studio klikněte v nabídce **zobrazení** na příkaz **prostředky**.

1. V **prostředky**dvakrát klikněte na prostředek pásu karet a zobrazte ho na návrhové ploše.

1. Na návrhové ploše klikněte pravým tlačítkem myši na nabídku tlačítka aplikace a pak klikněte na **vlastnosti**.

## <a name="application-button-properties"></a>Vlastnosti tlačítka aplikace

Následující tabulka definuje vlastnosti tlačítka aplikace.

|Vlastnost|Definice|
|--------------|----------------|
|**Tlačítka**|Obsahuje kolekci až tří tlačítek, která se zobrazí v pravém dolním rohu nabídky aplikace.|
|**Popisku**|Určuje text ovládacího prvku. Na rozdíl od jiných elementů pásu karet není tlačítkem aplikace zobrazen text titulku. Místo toho se text používá pro usnadnění přístupu.|
|**Obrázek HDPI**|Určuje identifikátor ikony tlačítka aplikace s vysokými tečkami na palec (HDPI). Když aplikace běží na monitoru s vysokým rozlišením DPI, použije se místo **Image** **HDPI obrázek** .|
|**HDPI velké obrázky**|Určuje identifikátor velkých imagí s vysokým rozlišením DPI. Když aplikace běží na monitoru s vysokým rozlišením DPI, místo **velkých imagí**se použije **HDPI velké obrázky** .|
|**HDPI malé obrázky**|Určuje identifikátor malých obrázků s vysokým rozlišením DPI. Když je aplikace spuštěná na monitoru s vysokým rozlišením DPI, místo **malých imagí**se použije **HDPI malý obrázek** .|
|**ID**|Určuje identifikátor ovládacího prvku.|
|**Obrázek**|Určuje identifikátor ikony tlačítka aplikace. Ikona je 32 bitová mapa 26x26 s průhledností alfa. Průhledné části ikony jsou zvýrazněné, když na tlačítko aplikace kliknete nebo najedete myší.|
|**Klíče**|Určuje řetězec, který se zobrazí, když je povolena navigace s tipem na klíč. Navigace s popisem klíče je povolená, když stisknete klávesu ALT.|
|**Velké obrázky**|Určuje identifikátor obrázku, který obsahuje řadu ikon 32x32. Ikony jsou používány tlačítky v kolekci Main Items.|
|**Hlavní položky**|Obsahuje kolekci položek nabídky, které se zobrazí v nabídce aplikace.|
|**Titulek MRU**|Určuje text zobrazený na panelu seznamu poslední.|
|**Malé obrázky**|Určuje identifikátor obrázku, který obsahuje řadu 16 ikon. Ikony jsou používány tlačítky v kolekci tlačítek.|
|**Použití**|Povolí nebo zakáže poslední panel seznamu. V nabídce aplikace se zobrazí panel poslední seznam.|
|**Délk**|Určuje šířku v pixelech nedávných panelů seznamu.|

Nabídka aplikace se nezobrazuje na návrhové ploše. Chcete-li jej zobrazit, musíte buď zobrazit náhled pásu karet, nebo spustit aplikaci.

#### <a name="to-preview-the-ribbon-control"></a>Náhled ovládacího prvku pás karet

- Na **panelu nástrojů editoru pásu karet**klikněte na tlačítko **testovat pás karet**.

## <a name="see-also"></a>Viz také:

[Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)
