---
title: Použití seznamů obrázků v ovládacím prvku rozšířené pole se seznamem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c9a701871631fead48c22b1ffb2cbc3c386b960
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383342"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>Použití seznamů obrázků v ovládacím prvku rozšířené pole se seznamem
Hlavní funkce ovládací prvky rozšířeného pole se seznamem je možnost k přidružení obrázků ze seznamu obrázků s jednotlivé položky v ovládacím prvku pole se seznamem. Každá položka je možné zobrazit tři různé bitové kopie: jednu pro vybraném stavu, jednu pro jeho nevybrané stavu a třetí pro bitovou kopii překrytí.  
  
 Následující postup přidruží seznamu obrázků s ovládacím prvku rozšířené pole se seznamem:  
  
### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>Chcete-li přidružit seznamu obrázků s ovládacím prvku rozšířené pole se seznamem  
  
1.  Vytvořit nového seznamu obrázků (nebo použijte existující objekt seznamu image), pomocí [CImageList](../mfc/reference/cimagelist-class.md) konstruktor a ukládání výsledné ukazatele.  
  
2.  Inicializace nového objektu seznamu image voláním [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Následující kód je jedním z příkladů tohoto volání.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]  
  
3.  Přidejte volitelné bitových kopií pro všechny možné stavy: vybrané nebo nevybrané a překrytí. Následující kód přidá tři předdefinované bitové kopie.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]  
  
4.  Přidružení seznamu obrázků s ovládacím prvkem pomocí volání [CComboBoxEx::SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist).  
  
 Jakmile nebyl seznamu obrázků s ovládacím prvku, můžete zadat jednotlivě bitové kopie, kterou každá položka bude používat pro tři možné stavy. Další informace najdete v tématu [nastavení obrázků pro jednotlivé položky](../mfc/setting-the-images-for-an-individual-item.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

