---
title: Použití seznamu obrázků s ovládacím prvkem matrice | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1786c89f4ec9cf1c0908dac5d81858d5b2e6b7db
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950703"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>Použití seznamu obrázků s ovládacím prvkem matrice
Každé vzdálené matrice může obsahovat mimo jiné, bitovou kopii ze seznamu přidruženou bitovou kopii. Následující postup popisuje nezbytné kroky pro zobrazení ve svazku matrice bitovou kopii.  
  
### <a name="to-display-images-in-a-rebar-band"></a>Pro zobrazení obrázků ve svazku matrice  
  
1.  Seznam obrázků připojit k vaší objekt ovládacího prvku matrice tím, že zavoláte na [SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist), předávání ukazatel do existujícího seznamu bitové kopie.  
  
2.  Změnit **REBARBANDINFO** struktura přiřadit matrice vzdálené bitovou kopii:  
  
    -   Nastavte *fMask* člena `RBBIM_IMAGE`, zahrnout další příznaky podle potřeby pomocí bitový operátor OR.  
  
    -   Nastavte *iImage* člena do seznamu index bitové kopie bitové kopie, který se má zobrazit.  
  
3.  Inicializuje všechny zbývající členy data, jako je například velikost, text a popisovač okna obsažené podřízené nezbytné informace.  
  
4.  Vložit nový vzdálené správy (s bitovou kopii) pomocí volání [CReBarCtrl::InsertBand](../mfc/reference/crebarctrl-class.md#insertband), předejte **REBARBANDINFO** struktury.  
  
 V následujícím příkladu se předpokládá, že existující objekt seznamu bitové kopie se dvě bitové kopie, se připojil k objekt ovládacího prvku matrice (`m_wndReBar`). Nové vzdálené matrice (definované `rbi`), který obsahuje bitovou kopii první, přidá se pomocí volání `InsertBand`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

