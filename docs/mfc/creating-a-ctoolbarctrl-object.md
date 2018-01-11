---
title: "Vytvoření objektu CToolBarCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CToolBarCtrl
dev_langs: C++
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e86fad8191c4dea2eed3ae34ec96ed853ac1deae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-ctoolbarctrl-object"></a>Vytvoření objektu CToolBarCtrl
[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objekty obsahují několik interních datových strukturách – seznam bitmap tlačítko bitové kopie, seznam řetězců, popisku tlačítka a seznam `TBBUTTON` struktury – které přidružit bitovou kopii nebo řetězec s pozice, styl a stavu, a ID příkazu tlačítka. Jednotlivých prvků tyto datové struktury odkazuje na index počítaný od nuly. Abyste mohli používat `CToolBarCtrl` objektu, musíte nastavit tyto datové struktury. Seznam datové struktury najdete v tématu [ovládací prvky panelu nástrojů](controls-mfc.md) ve Windows SDK. Seznam řetězců, můžete použít pouze pro tlačítko popisky; řetězce nelze načíst z panelu nástrojů.  
  
 Použít `CToolBarCtrl` objektu, bude obvykle postupujte podle těchto kroků:  
  
### <a name="to-use-a-ctoolbarctrl-object"></a>Použití objektu CToolBarCtrl  
  
1.  Vytvořit [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objektu.  
  
2.  Volání [vytvořit](../mfc/reference/ctoolbarctrl-class.md#create) vytvoření Windows běžné ovládací prvek panelu nástrojů a připojte ji k `CToolBarCtrl` objektu. Pokud chcete pro tlačítka rastrové obrázky, přidat bitmap tlačítka na panel nástrojů voláním [AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap). Pokud chcete řetězec popisky pro tlačítka, přidejte řetězce na panel nástrojů voláním [addstring –](../mfc/reference/ctoolbarctrl-class.md#addstring) nebo [AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings). Po volání `AddString` nebo `AddStrings`, by měly volat [AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize) zajistí, že řetězec nebo řetězce se objeví.  
  
3.  Přidání struktury tlačítka na panel nástrojů voláním [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons).  
  
4.  Pokud chcete popisy, zpracování **TTN_NEEDTEXT** zprávy v okně Vlastník panelu nástrojů, jak je popsáno v [zpracování oznámení popisů Tip](../mfc/handling-tool-tip-notifications.md).  
  
5.  Pokud chcete, aby vaše uživatele jako možnosti přizpůsobení panelu nástrojů, zpracování zpráv s oznámením přizpůsobení v okně vlastníka jak je popsáno v [zpracování oznámení o přizpůsobení](../mfc/handling-customization-notifications.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

