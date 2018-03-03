---
title: "Zajištění podpory přetažení a přetažení u položek záhlaví | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fd1ac2171a13610ee3aeabed12f5348089a57491
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Zajištění podpory přetažení u položek záhlaví
Kvůli zajištění podpory přetažení a přetažení u položek záhlaví, zadejte `HDS_DRAGDROP` stylu. Podpory a přetažení u položek záhlaví dává uživateli možnost ke změně pořadí položek záhlaví ovládacího prvku záhlaví. Výchozí chování poskytuje poloprůhledných přetáhněte obrázek položky záhlaví přetažen a vizuální indikátor nové pozice, pokud hlavička položka byla vynechána.  
  
 Jak se běžné funkce přetahování myší, můžete rozšířit výchozí chování a přetažení zpracování **HDN_BEGINDRAG** a **HDN_ENDDRAG** oznámení. Můžete také přizpůsobit vzhled obrázku přetáhněte přepsání [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) – členská funkce.  
  
> [!NOTE]
>  Pokud pro ovládací prvek embedded záhlaví v ovládacím prvku seznamu jsou zajištění podpory přetažení myší, naleznete v části rozšířený styl [změna stylů ovládacího prvku seznam](../mfc/changing-list-control-styles.md) tématu.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)

