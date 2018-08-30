---
title: Změna stylů ovládacího prvku seznam | Dokumentace Microsoftu
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
ms.openlocfilehash: 4919d9fd947a489ee9535abd5aa57d7861ba5a37
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197991"
---
# <a name="changing-list-control-styles"></a>Změna stylů ovládacího prvku seznam
Můžete změnit styl okna ovládacího prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)) kdykoli po jeho vytvoření. Změnou stylu okna změníte typ zobrazení, které používá ovládací prvek. Například pro emulaci Explorer, je může zadat položky nabídky nebo tlačítka panelu nástrojů pro přepínání mezi různá zobrazení ovládacího prvku: zobrazení ikon, zobrazení seznamu a tak dále.  
  
 Například když uživatel vybere položku nabídky, které může uskutečnit volání [GetWindowLong](https://msdn.microsoft.com/library/windows/desktop/ms633584) načíst aktuální styl ovládacího prvku a poté zavolejte [SetWindowLong](https://msdn.microsoft.com/library/windows/desktop/ms633591) resetovat styl. Další informace najdete v tématu [ovládací prvky zobrazení pomocí seznamu](/windows/desktop/Controls/using-list-view-controls) v sadě Windows SDK.  
  
 K dispozici styly jsou uvedeny v [vytvořit](../mfc/reference/clistctrl-class.md#create). Styly **jen**, **LVS_SMALLICON**, **LVS_LIST**, a **LVS_REPORT** určit čtyři seznamy ovládacího prvku.  
  
## <a name="extended-styles"></a>Rozšířené styly  
 Kromě standardních stylů pro ovládací prvek seznamu je další sady, jen rozšířené styly. Tyto styly podrobněji [rozšířené styly zobrazení seznamu](/windows/desktop/Controls/extended-list-view-styles) v sadě Windows SDK poskytují celou řadu užitečných funkcí, které přizpůsobit chování ovládacího prvku seznamu. K implementaci chování stylu (například výběr při přechodu myší), ujistěte se, volání [CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), předání potřebných style. Následující příklad ukazuje volání funkce:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]  
  
> [!NOTE]
>  Pro výběr při najetí myší na práci, musíte také mít **LVS_EX_ONECLICKACTIVATE** nebo **LVS_EX_TWOCLICKACTIVATE** zapnuté.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

