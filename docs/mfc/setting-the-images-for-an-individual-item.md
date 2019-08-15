---
title: Nastavení obrázků pro jednotlivé položky
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
ms.openlocfilehash: 177c06acfe665a43921b19407d9d357d4545e748
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511285"
---
# <a name="setting-the-images-for-an-individual-item"></a>Nastavení obrázků pro jednotlivé položky

Různé typy obrázků, které používá rozšířená položka pole se seznamem, jsou určeny hodnotami v *iImage*, *iSelectedImage*a *IOverlay* členů struktury [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) . Každá hodnota je index obrázku v přidruženém seznamu obrázků ovládacího prvku. Ve výchozím nastavení jsou tito členové nastaveni na 0, což způsobí, že ovládací prvek zobrazí pro položku žádný obrázek. Pokud chcete použít obrázky pro konkrétní položku, můžete změnit strukturu odpovídajícím způsobem při vložení položky pole se seznamem nebo úpravou existující položky pole se seznamem.

## <a name="setting-the-image-for-a-new-item"></a>Nastavení obrázku pro novou položku

Pokud vkládáte novou položku, inicializujte členy struktury *iImage*, *iSelectedImage*a *IOverlay* se správnými hodnotami a poté vložte položku s voláním [atributu CComboBoxEx:: InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).

Následující příklad vloží novou rozšířenou položku pole se seznamem (`cbi`) do rozšířeného ovládacího prvku pole se seznamem`m_comboEx`() a poskytne indexy pro všechny tři stavy imagí:

[!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]

## <a name="setting-the-image-for-an-existing-item"></a>Nastavení obrázku pro existující položku

Pokud upravujete existující položku, je nutné pracovat s členem *masky* struktury **COMBOBOXEXITEM** .

#### <a name="to-modify-an-existing-item-to-use-images"></a>Úprava existující položky pro použití imagí

1. Deklarujte strukturu **COMBOBOXEXITEM** a nastavte datový člen *masky* na hodnoty, které vás zajímají.

1. Pomocí této struktury proveďte volání [atributu CComboBoxEx:: GetItem](../mfc/reference/ccomboboxex-class.md#getitem).

1. Upravte pomocí příslušných hodnot *masku*, *iImage*a *iSelectedImage* členy nově vrácené struktury.

1. Zavolejte do [atributu CComboBoxEx:: SetItem](../mfc/reference/ccomboboxex-class.md#setitem)a předejte upravenou strukturu.

Následující příklad demonstruje tento postup záměnam vybraného a nevybraného obrázku třetí rozšířené položky pole se seznamem:

[!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]

## <a name="see-also"></a>Viz také:

[Používání atributu CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
