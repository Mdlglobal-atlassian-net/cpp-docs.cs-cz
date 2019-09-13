---
title: 'Postupy: Přizpůsobení panelu nástrojů Rychlý přístup'
ms.date: 09/07/2019
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
ms.openlocfilehash: 8b2eb6f7c80c77f69e2bbb65b7bb31a385014c8c
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907784"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>Postupy: Přizpůsobení panelu nástrojů Rychlý přístup

Panel nástrojů Rychlý přístup (QAT) je přizpůsobitelný panel nástrojů, který obsahuje sadu příkazů, které se zobrazují buď vedle tlačítka aplikace, nebo pod kartami kategorií. Na následujícím obrázku vidíte typický panel nástrojů Rychlý přístup.

![Panel nástrojů Rychlý přístup k pásu karet MFC](../mfc/media/quick_access_toolbar.png "Panel nástrojů Rychlý přístup k pásu karet MFC")

Chcete-li přizpůsobit panel nástrojů Rychlý přístup, otevřete jej v okně **vlastnosti** , upravte jeho příkazy a potom zobrazte náhled ovládacího prvku pásu karet.

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>Otevření panelu nástrojů Rychlý přístup v okno Vlastnosti

1. V aplikaci Visual Studio klikněte v nabídce **zobrazení** na příkaz **prostředky**.

1. V **prostředky**dvakrát klikněte na prostředek pásu karet a zobrazte ho na návrhové ploše.

1. Na návrhové ploše klikněte pravým tlačítkem myši na nabídku panelu nástrojů Rychlý přístup a pak klikněte na **vlastnosti**.

## <a name="quick-access-toolbar-properties"></a>Vlastnosti panelu nástrojů Rychlý přístup

Následující tabulka definuje vlastnosti panelu nástrojů Rychlý přístup.

|Vlastnost|Definice|
|--------------|----------------|
|Pozice QAT|Určuje umístění panelu nástrojů Rychlý přístup při spuštění aplikace. Pozice může být buď **nad** , nebo **pod** ovládacím prvkem pásu karet.|
|QAT položky|Určuje příkazy, které jsou k dispozici pro panel nástrojů Rychlý přístup.|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>Přidání nebo odebrání příkazů na panelu nástrojů Rychlý přístup

1. V okně **vlastnosti** klikněte na položku **QAT položky**a potom klikněte na tlačítko se třemi tečkami **(...)** .

1. V dialogovém okně **Editor položek QAT** pomocí tlačítek **Přidat** a **Odebrat** upravte seznam příkazů na panelu nástrojů Rychlý přístup.

1. Pokud se má příkaz Zobrazit na panelu nástrojů Rychlý přístup i v nabídce panelu nástrojů Rychlý přístup, zaškrtněte políčko vedle příkazu. Pokud chcete, aby se příkaz zobrazil pouze v nabídce, zrušte zaškrtnutí políčka.

## <a name="previewing-the-ribbon"></a>Náhled pásu karet

Příkazy panelu nástrojů Rychlý přístup se nezobrazují na návrhové ploše. Chcete-li je zobrazit, musíte buď zobrazit náhled pásu karet, nebo spustit aplikaci.

#### <a name="to-preview-the-ribbon-control"></a>Náhled ovládacího prvku pás karet

- Na **panelu nástrojů editoru pásu karet**klikněte na tlačítko **testovat pás karet**.

## <a name="see-also"></a>Viz také:

[Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)
