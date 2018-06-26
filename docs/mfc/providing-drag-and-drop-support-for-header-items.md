---
title: Zajištění podpory přetažení a přetažení u položek záhlaví | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6bf21021e204a6caf298453bab42db2aedff409c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928417"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Zajištění podpory přetažení u položek záhlaví
Kvůli zajištění podpory přetažení a přetažení u položek záhlaví, zadejte hds_dragdrop – styl. Podpory a přetažení u položek záhlaví dává uživateli možnost ke změně pořadí položek záhlaví ovládacího prvku záhlaví. Výchozí chování poskytuje poloprůhledných přetáhněte obrázek položky záhlaví přetažen a vizuální indikátor nové pozice, pokud hlavička položka byla vynechána.  
  
 Jako s běžné funkce přetahování myší, můžete rozšířit výchozí chování a přetažení zpracování HDN_BEGINDRAG a HDN_ENDDRAG oznámení. Můžete také přizpůsobit vzhled obrázku přetáhněte přepsání [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) – členská funkce.  
  
> [!NOTE]
>  Pokud pro ovládací prvek embedded záhlaví v ovládacím prvku seznamu jsou zajištění podpory přetažení myší, naleznete v části rozšířený styl [změna stylů ovládacího prvku seznam](../mfc/changing-list-control-styles.md) tématu.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)

