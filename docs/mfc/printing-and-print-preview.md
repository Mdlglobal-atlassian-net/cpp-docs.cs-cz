---
title: "Tisk a náhled tisku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fb0b46526921e820df1c0618106667a46cf135be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="printing-and-print-preview"></a>Tisk a náhled tisku
MFC podporuje tisku a přehled tisku pro váš program dokumenty pomocí třídy [CView](../mfc/reference/cview-class.md). Pro základní tisku a tiskového náhledu, jednoduše přepíší třídy zobrazení [OnDraw –](../mfc/reference/cview-class.md#ondraw) členská funkce, které je nutné provést přesto. Tuto funkci můžete zakreslit zobrazení na obrazovce, kontextu zařízení tiskárny skutečné tiskárny, nebo do kontextu zařízení, která simuluje tiskárny na obrazovce.  
  
 Můžete také přidat kód pro správu Tisk vícestránkového dokumentu a preview, přejdete na tištěných dokumentů a přidání záhlaví a zápatí do nich.  
  
 Této rodině článků vysvětluje způsob implementace tisk v Microsoft Foundation Class Library (MFC) a jak chcete využít výhod architektura pro tisk již součástí rozhraní. Články také vysvětlují, jak MFC podporuje snadno implementace funkce náhledu tisku a jak můžete použít a změnit této funkce.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Tisk](../mfc/printing.md)  
  
-   [Architektura náhledu tisku](../mfc/print-preview-architecture.md)  
  
-   [Ukázka](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Viz také  
 [Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)