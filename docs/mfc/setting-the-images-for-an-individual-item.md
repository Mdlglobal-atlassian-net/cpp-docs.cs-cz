---
title: "Nastavení obrázků pro jednotlivé položky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dec67e2ff5423213645b2e5bb8493198eb53dff9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="setting-the-images-for-an-individual-item"></a>Nastavení obrázků pro jednotlivé položky
Různé typy obrázků použitých položkou pole rozšířeného pole se seznamem, které jsou určeny podle hodnot v `iImage`, **iSelectedImage**, a **iOverlay** členy [COMBOBOXEXITEM ](http://msdn.microsoft.com/library/windows/desktop/bb775746) struktura. Každá hodnota je index bitové kopie v seznamu přidruženou bitovou kopii ovládacího prvku. Tito členové jsou standardně nastavena na hodnotu 0, způsobuje ovládací prvek zobrazí žádný obrázek pro položku. Pokud chcete použít Image pro konkrétní položky, můžete upravit strukturu odpovídajícím způsobem, při vkládání položky pole se seznamem nebo úpravou existující položky pole se seznamem.  
  
## <a name="setting-the-image-for-a-new-item"></a>Nastavení bitovou kopii pro novou položku  
 Při vkládání nové položky, inicializovat `iImage`, **iSelectedImage**, a **iOverlay** struktury členy s správné hodnoty a potom vložte položka se volání [ CComboBoxEx::InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).  
  
 Následující příklad vloží novou položku pole rozšířeného pole se seznamem (`cbi`) do pole ovládacího prvku rozšířené pole se seznamem (`m_comboEx`), poskytuje indexů pro všechny tři image stavy:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]  
  
## <a name="setting-the-image-for-an-existing-item"></a>Nastavení bitovou kopii pro existující položky  
 Pokud upravujete stávající položku, budete muset pracovat **maska** členem **COMBOBOXEXITEM** struktury.  
  
#### <a name="to-modify-an-existing-item-to-use-images"></a>Chcete-li upravit existující položku, kterou chcete použít Image  
  
1.  Deklarace **COMBOBOXEXITEM** struktury a nastavte **maska** – datový člen na hodnoty se zajímáte úpravy.  
  
2.  Pomocí této struktuře provést volání [CComboBoxEx::GetItem](../mfc/reference/ccomboboxex-class.md#getitem).  
  
3.  Změnit **maska**, `iImage`, a **iSelectedImage** členů struktury nově vrácený pomocí příslušné hodnoty.  
  
4.  Ujistěte se, volání [CComboBoxEx::SetItem](../mfc/reference/ccomboboxex-class.md#setitem), předejte ve struktuře upravené.  
  
 Následující příklad ukazuje podle odkládací Image vybrané a nezaškrtnuté políčko položky třetí rozšířeného pole se seznamem, tento postup:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)
