---
title: Nastavení obrázků pro jednotlivé položky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c64ab33f053c941bd5332269d4c952b3a318cb6b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209301"
---
# <a name="setting-the-images-for-an-individual-item"></a>Nastavení obrázků pro jednotlivé položky
Různé druhy obrázky používané v rozšířené pole se seznamem položky pole se určují podle hodnot v *iImage*, *iSelectedImage*, a *spojek není použit* členů [ COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) struktury. Každá hodnota je index obrázku v seznamu přidružené image z ovládacího prvku. Tyto členy jsou ve výchozím nastavení, nastavte na hodnotu 0, způsobí ovládací prvek pro zobrazení bez obrázku pro položku. Pokud chcete použít obrázky pro konkrétní položky, můžete to strukturu upravit odpovídajícím způsobem, při vkládání položky pole se seznamem nebo úpravou existující položky pole se seznamem.  
  
## <a name="setting-the-image-for-a-new-item"></a>Obrázek nastavení pro novou položku  
 Pokud vkládáte nová položka, inicializovat *iImage*, *iSelectedImage*, a *spojek není použit* nahraďte odpovídajícími hodnotami členy struktury a poté je vkládat položky pomocí volání [CComboBoxEx::InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).  
  
 V následujícím příkladu vloží nové položky pole Rozšířené pole se seznamem (`cbi`) do pole ovládacího prvku rozšířené pole se seznamem (`m_comboEx`), poskytuje indexy pro všechny tři stavy bitové kopie:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]  
  
## <a name="setting-the-image-for-an-existing-item"></a>Obrázek nastavení pro existující položku  
 Pokud chcete upravit existující položka, budete muset pracovat *maska* členem **COMBOBOXEXITEM** struktury.  
  
#### <a name="to-modify-an-existing-item-to-use-images"></a>Chcete-li upravit existující položku, kterou chcete použít Image  
  
1.  Deklarace **COMBOBOXEXITEM** struktury a nastavit *maska* datový člen hodnoty se zajímáte úpravy.  
  
2.  Pomocí této struktury uskutečnit volání [CComboBoxEx::GetItem](../mfc/reference/ccomboboxex-class.md#getitem).  
  
3.  Upravit *maska*, *iImage*, a *iSelectedImage* členové nově vrácené struktury pomocí příslušné hodnoty.  
  
4.  Volání [CComboBoxEx::SetItem](../mfc/reference/ccomboboxex-class.md#setitem)a předejte změněné struktury.  
  
 Následující příklad ukazuje tento postup pomocí výměny vybrané a nevybrané obrázky třetí položka pole Rozšířené pole se seznamem:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

