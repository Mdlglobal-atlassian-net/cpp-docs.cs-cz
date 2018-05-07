---
title: 'Postupy: přizpůsobení panelu nástrojů Rychlý přístup | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0faa3a0fb66c4379824a6be190175b10e0415474
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>Postupy: Přizpůsobení panelu nástrojů Rychlý přístup
Rychlý přístup k panelu nástrojů (QAT) je přizpůsobitelné nástrojů, který obsahuje sadu příkazů, které jsou buď zobrazí vedle tlačítka aplikace nebo na kartách kategorie. Následující obrázek znázorňuje typické nástrojů Rychlý přístup.  
  
 ![Nástrojů Rychlý přístup k pásu karet MFC](../mfc/media/quick_access_toolbar.png "quick_access_toolbar")  
  
 Chcete-li přizpůsobit panel nástrojů Rychlý přístup, otevřete ho v **vlastnosti** okně upravit jeho příkazy a pak zobrazte náhled ovládacího prvku pásu karet.  
  
### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>Chcete-li otevřít panel nástrojů Rychlý přístup v okně vlastností  
  
1.  V sadě Visual Studio na **zobrazení** nabídky, klikněte na tlačítko **zobrazení prostředků**.  
  
2.  V **zobrazení prostředků**, dvakrát klikněte na prostředek pásu karet, která se zobrazí na návrhovou plochu.  
  
3.  Na návrhové ploše, klikněte pravým tlačítkem na panelu nástrojů Rychlý přístup k nabídce a potom klikněte na **vlastnosti**.  
  
## <a name="quick-access-toolbar-properties"></a>Vlastnosti panelu nástrojů Rychlý přístup  
 Následující tabulka definuje vlastnosti panel nástrojů Rychlý přístup.  
  
|Vlastnost|Definice|  
|--------------|----------------|  
|QAT pozice|Určuje pozici panelu nástrojů Rychlý přístup při spuštění aplikace. Pozice může být buď **výše** nebo **pod** ovládacího prvku pásu karet.|  
|QAT položky|Určuje příkazy, které jsou k dispozici pro panel nástrojů Rychlý přístup.|  
  
#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>Přidat nebo odebrat příkazy na panelu nástrojů Rychlý přístup  
  
1.  V **vlastnosti** okně klikněte na tlačítko **QAT položky**a potom klikněte na tlačítko se třemi tečkami **(...)** .  
  
2.  V **QAT položky Editor** dialogové okno, použijte **přidat** a **odebrat** Chcete-li upravit seznam příkazů na panelu nástrojů Rychlý přístup.  
  
3.  Pokud chcete, aby příkaz zobrazí na panelu nástrojů Rychlý přístup a v nabídce nástrojů Rychlý přístup, zaškrtněte políčko vedle příkazu. Pokud chcete příkaz Zobrazit pouze v nabídce, zrušte zaškrtnutí pole.  
  
## <a name="previewing-the-ribbon"></a>Zobrazení náhledu na pásu karet  
 Rychlý přístup k panelu nástrojů příkazy nejsou zobrazeny na návrhovou plochu. K jejich zobrazení, musíte zobrazit náhled na pásu karet nebo spuštění aplikace.  
  
#### <a name="to-preview-the-ribbon-control"></a>Zobrazte náhled ovládacího prvku pásu karet  
  
-   Na **panelu nástrojů editoru pásu karet**, klikněte na **testovací pásu karet**.  
  
## <a name="see-also"></a>Viz také  
 [Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)

