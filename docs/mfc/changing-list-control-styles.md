---
title: Změna stylů ovládacího prvku seznam | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9d93511ad4f4ca835e09b6eaa3f612f0888e844
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344839"
---
# <a name="changing-list-control-styles"></a>Změna stylů ovládacího prvku seznam
Můžete změnit styl okna ovládacího prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)) kdykoli po jejím vytvoření. Změnou styl okna změníte typ zobrazení, které používá ovládacího prvku. Například emulovat v Exploreru, může zadáte položky nabídky nebo tlačítka panelu nástrojů pro přepínání mezi různá zobrazení ovládacího prvku: zobrazení ikon, zobrazení seznamu a tak dále.  
  
 Například pokud uživatel vybere vaší položky nabídky, můžete dokonce vytvářet volání [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) načíst aktuální styl ovládacího prvku a pak zavolají [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) resetovat styl. Další informace najdete v tématu [ovládací prvky zobrazení pomocí seznamu](http://msdn.microsoft.com/library/windows/desktop/bb774736) ve Windows SDK.  
  
 Styly k dispozici jsou uvedeny v [vytvořit](../mfc/reference/clistctrl-class.md#create). Styly `LVS_ICON`, `LVS_SMALLICON`, `LVS_LIST`, a `LVS_REPORT` určit čtyři seznamy řízení.  
  
## <a name="extended-styles"></a>Rozšířené styly  
 Kromě standardní styly pro ovládací prvek seznamu je jinou sadu, označuje jako rozšířené styly. Tyto styly popsané v [rozšířené styly zobrazení seznamu](http://msdn.microsoft.com/library/windows/desktop/bb774732) ve Windows SDK poskytují řadu užitečných funkcí, které přizpůsobují chování ovládacího prvku seznam. Pokud chcete implementovat chování určité styl (například hover výběr), ujistěte se, volání [CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), předávání styl potřebné. Následující příklad ukazuje volání funkce:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]  
  
> [!NOTE]
>  Pro výběr hover pracovat, je také nutné mít buď **LVS_EX_ONECLICKACTIVATE** nebo **LVS_EX_TWOCLICKACTIVATE** zapnutý.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

