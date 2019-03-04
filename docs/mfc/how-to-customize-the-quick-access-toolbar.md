---
title: 'Postupy: Přizpůsobení panelu nástrojů Rychlý přístup'
ms.date: 11/19/2018
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
ms.openlocfilehash: c53e405eafe310c0bfc03a916ab85181ae67a34b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300711"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>Postupy: Přizpůsobení panelu nástrojů Rychlý přístup

Panel nástrojů Rychlý přístup (QAT) je přizpůsobitelný panel nástrojů, který obsahuje sadu příkazů, které jsou buď zobrazí vedle tlačítka, aplikace nebo na kartách kategorie. Následující obrázek znázorňuje typický panelu nástrojů Rychlý přístup.

![Panel nástrojů Rychlý přístup pásu karet MFC](../mfc/media/quick_access_toolbar.png "panel nástrojů Rychlý přístup knihovny MFC pásu karet")

Přizpůsobení panelu nástrojů Rychlý přístup, otevřete ho **vlastnosti** okna, upravte příkazy a pak zobrazte náhled ovládacího prvku pásu karet.

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>Chcete-li otevřít panel nástrojů Rychlý přístup v okně Vlastnosti

1. V sadě Visual Studio na **zobrazení** nabídky, klikněte na tlačítko **zobrazení prostředků**.

1. V **zobrazení prostředků**, dvakrát klikněte na prostředek pásu karet se zobrazí na návrhové ploše.

1. Na návrhové ploše, klikněte pravým tlačítkem na panelu nástrojů Rychlý přístup k nabídce a potom klikněte na **vlastnosti**.

## <a name="quick-access-toolbar-properties"></a>Vlastnosti panelu nástrojů Rychlý přístup

Následující tabulka definuje vlastnosti panelu nástrojů Rychlý přístup.

|Vlastnost|Definice|
|--------------|----------------|
|Pozici panelu nástrojů Rychlý přístup|Určuje pozici panelu nástrojů Rychlý přístup při spuštění aplikace. Umístění může být buď **nad** nebo **níže** ovládací prvek pásu karet.|
|Položky panelu nástrojů Rychlý přístup|Určuje příkazy, které jsou k dispozici pro panel nástrojů Rychlý přístup.|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>Chcete-li přidat nebo odebrat příkazy na panelu nástrojů Rychlý přístup

1. V **vlastnosti** okna, klikněte na tlačítko **QAT Items**a potom klikněte na tlačítko se třemi tečkami **(...)** .

1. V **Edito položek** dialogové okno, použijte **přidat** a **odebrat** tlačítka Upravit seznam příkazů na panelu nástrojů Rychlý přístup.

1. Pokud chcete příkazu se zobrazí na panelu nástrojů Rychlý přístup a nabídky panelu nástrojů Rychlý přístup, zaškrtněte políčko vedle příkazu. Pokud chcete příkazu se zobrazí pouze v nabídce, zrušte zaškrtnutí pole.

## <a name="previewing-the-ribbon"></a>Náhled pásu karet

Rychlé příkazy nástrojů přístup se nezobrazují na návrhové ploše. K jejich zobrazení, musíte zobrazit náhled pásu karet nebo spusťte aplikaci.

#### <a name="to-preview-the-ribbon-control"></a>Na pásu karet ovládací prvek náhledu

- Na **nástrojů editoru pásu karet**, klikněte na tlačítko **testovat pás karet**.

## <a name="see-also"></a>Viz také:

[Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)
