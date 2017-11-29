---
title: "Seznam vlastností a stránky vlastností v MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 93288308f78d719c4b2cad60ac4a95a607726f4f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Seznamy vlastností a stránky vlastností v prostředí MFC
Seznam vlastností, také známé jako karta dialogového okna, je dialogové okno, které obsahuje stránky vlastností. Každé stránce vlastnosti je založena na prostředku šablony dialogové okno a obsahuje ovládací prvky. Na stránce je uzavřen s karty v horní části. Na kartě názvy stránky a určuje jeho účel. Uživatelé kliknou na kartě v seznamu vlastností vyberte sadu ovládacích prvků.  
  
 Skupina ovládacích prvků v seznamu vlastností do smysluplný nastaví pomocí stránky. Seznam vlastností obsažené obvykle obsahuje několik ovládacích prvků vlastní. Toto platí pro všechny stránky.  
  
 Seznam vlastností jsou založeny na třídě [cpropertysheet –](../mfc/reference/cpropertysheet-class.md). Stránky vlastností jsou založeny na třídě [CPropertyPage](../mfc/reference/cpropertypage-class.md).  
  
 Seznam vlastností je zvláštní druh okno, které se obecně používají k úpravě atributy některé externí objektu, například aktuální výběr v zobrazení. Seznam vlastností obsahuje tři hlavní části: dialogovém okně obsahující jeden nebo více vlastností stránky zobrazené současně a karty v horní části každé stránce, které uživatel klikne na této stránce vyberte. Seznam vlastností jsou užitečné v situacích, kdy máte několik podobné skupiny nastavení nebo změnu. Seznam vlastností skupiny informace jednoduché k pochopení způsobem.  
  
> [!NOTE]
>  Pokud chcete zobrazit seznam vlastností pomocí `CPropertySheet::DoModal`, systém může generovat první odpovídající výjimce. K této výjimce dochází, protože systém se pokouší změnit [styly oken](../mfc/reference/styles-used-by-mfc.md#window-styles) objektu dříve, než se vytvoří objekt. Další informace o výjimku a také jak tomu zamezit nebo ji zpracovat najdete v tématu [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal).  
  
## <a name="see-also"></a>Viz také  
 [Seznam vlastností](../mfc/property-sheets-mfc.md)
