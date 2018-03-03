---
title: "Vytvoří zobrazení (MFC) | Microsoft Docs"
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
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e784858c17c01c8a538edebdb15a89863d16438
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="form-views-mfc"></a>Zobrazení formulářů (MFC)
Forms můžete přidat do žádné aplikace Visual C++, který podporuje knihovny MFC, včetně [aplikace založené na formulářích](../mfc/reference/creating-a-forms-based-mfc-application.md) (jedna třída jejichž zobrazení je odvozený od `CFormView`). Pokud nebyl vytvořen původně aplikace podporují formuláře, Visual C++ přidá tato podpora pro vás, když vložíte nového formuláře. V aplikaci SDI a MDI, který implementuje výchozí [document/view – architektura](../mfc/document-view-architecture.md), když uživatel vybere `New` příkaz (ve výchozím nastavení, na **souboru** nabídky), Visual C++ vyzývá uživatele k Vyberte z dostupných formulářů.  
  
 Pomocí aplikace SDI, když uživatel vybere `New` aktuální instanci formuláře pokračuje v činnosti, ale vytvořit novou instanci aplikace s vybraný formulář, pokud není nalezen jeden příkaz. V aplikaci MDI nadále spouštět, když uživatel vybere aktuální instance formuláře `New` příkaz.  
  
> [!NOTE]
>  Formuláře můžete vložit do aplikace založené na dialogové okno (jeden jejichž třídy dialogového okna je založený na `CDialog` a jeden v žádné zobrazení, které se implementuje třídu). Ale bez architektuře dokument/zobrazení Visual C++ neimplementuje automaticky **soubor**&#124; **Nové** funkce. Je nutné vytvořit způsob, jak uživateli zobrazit další způsoby, například implementací dialogové okno s použitím různých stránek vlastností.  
  
 Při vložení nového formuláře do vaší aplikace, Visual C++ provede následující akce:  
  
-   Vytvoří třídu na základě jedné z třídy styl formuláře, které zvolíte (`CFormView`, `CRecordView`, `CDaoRecordView`, nebo `CDialog`).  
  
-   Vytvoří prostředek dialogové okno s odpovídající styly (nebo můžete použít existující prostředku dialogového okna, která dosud nebyla spojeny s třídou).  
  
     Pokud zvolíte existující prostředek dialogové okno, musíte nastavit tyto styly pomocí stránku vlastností pro dialogové okno. Styly pro dialogové okno musí zahrnovat:  
  
     **Ws_child –**= On  
  
     `WS_BORDER`= Vypnuto  
  
     **Ws_visible –**= vypnuto  
  
     **Ws_caption – =**vypnuto  
  
 Pro aplikace založené na architektuře dokument/zobrazení **nového formuláře** příkazu (v zobrazení tříd klikněte pravým tlačítkem) také:  
  
-   Vytvoří **CDocument**– na základě – třída  
  
     Místo nutnosti vytvořit novou třídu, můžete použít všechny existující **CDocument**– na základě třídy ve vašem projektu.  
  
-   Generuje šablony dokumentu (odvozený z **CDocument**) s řetězcem, nabídky a ikony prostředky.  
  
     Můžete také vytvořit novou třídu, na které chcete vytvořit šablonu.  
  
-   Přidá volání **AddDocumentTemplate** ve vaší aplikaci `InitInstance` kódu.  
  
     Visual C++ přidá tento kód pro každý nový formulář vytvoříte, který přidá do seznamu dostupných formulářů formuláře, když uživatel vybere `New` příkaz. Tento kód obsahuje ID přidružených prostředků formuláře a názvy přidružené dokumentu, zobrazení a rámečku třídy, které společně tvoří nový objekt formuláře.  
  
     Šablony dokumentů sloužit jako připojení mezi dokumentů, oken s rámečkem a zobrazení. Pro jednotlivý dokument můžete vytvořit mnoho šablony.  
  
 Další informace naleznete v tématu:  
  
-   [Vytvoření aplikace založené na formulářích](../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [Vložení formuláře do projektu](../mfc/inserting-a-form-into-a-project.md)  
  
## <a name="see-also"></a>Viz také  
 [Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
