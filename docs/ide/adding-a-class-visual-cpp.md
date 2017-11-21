---
title: "Přidání třídy (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.classes.adding
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9dab2974d4d177580b0051338a20b9dacf113f89
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="adding-a-class-visual-c"></a>Přidání třídy (Visual C++)
Přidání třídy v projektu Visual C++ v **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt, klikněte na **přidat**a potom klikněte na **třída**. Tím se otevře [dialogové okno Přidat třídu](../ide/add-class-dialog-box.md) dialogové okno.  
  
 Když přidáte třídu, musíte zadat název, který se liší od třídy, které již existují v knihovně MFC nebo ATL. Pokud zadáte název, který již v knihovně existuje, Visual C++ zobrazí zprávu, která označuje, že zadaný název je vyhrazený.  
  
 Pokud projekt zásady vytváření názvů vyžaduje, abyste existující název, potom můžete právě změnit malá a velká písmena jeden nebo více v názvu protože Visual C++ je malá a velká písmena. Například i když nelze pojmenovat třídu `CDocument`, můžete ho pojmenovat `cdocument`.  
  
## <a name="what-kind-of-class-do-you-want-to-add"></a>Jaký druh třídy chcete přidat?  
 V **přidat třídu** dialogové okno, když rozšiřujete **Visual C++** uzlu v levém podokně se zobrazí několik seskupení nainstalovaných šablon. Zahrnout skupiny **CLR**, **ATL**, **MFC**, a **C++**. Když vyberete skupinu, se v prostředním podokně zobrazí seznam dostupných šablon v této skupině. Každá šablona obsahuje soubory a zdrojového kódu, které jsou požadovány pro třídu.  
  
 Chcete-li vygenerovat novou třídu, vyberte šablonu v prostředním podokně, zadejte název pro třídu v **název** pole a klikněte na tlačítko **přidat**. Tím se otevře **Průvodce přidáním třídy** , ve kterém můžete zadat možnosti pro třídu.  
  
-   Další informace o tom, jak vytvořit MFC – třídy najdete v tématu [třídy knihovny MFC](../mfc/reference/adding-an-mfc-class.md).  
  
-   Další informace o tom, jak vytvořit třídy ATL najdete v tématu [ATL Simple Object](../atl/reference/adding-an-atl-simple-object.md).  
  
> [!NOTE]
>  Šablona **přidání podpory knihovny ATL do MFC** nevytvoří třídu, ale nastaví projekt, který používá ATL. Další informace najdete v tématu [podpory knihovny ATL v projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
 Chcete-li C++ třídu, která nepoužívá MFC, ATL nebo CLR, použijte **třídami C++** šablony v **C++** skupiny nainstalovaných šablon. Další informace najdete v tématu [přidání obecnými třídami C++](../ide/adding-a-generic-cpp-class.md).  
  
 Dva druhy založené na formulářích třídy C++ jsou k dispozici. První z nich, [třídy CFormView](../mfc/reference/cformview-class.md) vytvoří třídy knihovny MFC. Druhý vytvoří třídy CLR Windows Forms.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření aplikací MFC založených na formulářích](../mfc/reference/creating-a-forms-based-mfc-application.md)   
 [Přidat dialogové okno – třída](../ide/add-class-dialog-box.md)   
 [Tvorba běžných projektů pomocí průvodců aplikací](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)