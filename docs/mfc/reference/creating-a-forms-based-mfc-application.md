---
title: Vytváření aplikací MFC založených na formulářích | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcforms.project
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5ee588d7fe90e5bfc39aa8e4ab7a7499b62ad98
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-forms-based-mfc-application"></a>Vytváření aplikací MFC založených na formulářích
Formulář je dialogové okno s ovládacími prvky, které může uživatel získávat přístup a které by mohly mít měnit data. Můžete vyvíjet aplikace, ve kterém si uživatel vybere ze několika formulářů. Běžně, formulářové aplikace umožňuje uživateli přístup k formulářům kliknutím **nový** z **souboru** nabídky. Dialogové okno aplikace, které uživateli neposkytují přístup k **nový** možnost **souboru** nabídky, je také považují za aplikace založené na formulářích.  
  
 Jedním dokumentem (SDI rozhraní), na základě formulářů aplikace umožňuje jenom jednu instanci příslušného formuláře ke spuštění v čase. Je možné spustit různé formuláře ve stejnou dobu z aplikace založené na formulářích SDI výběrem nového formuláře z **nový** možnost **souboru** nabídky.  
  
 Pokud vytvoříte rozhraní více dokumentů (MDI), aplikace založené na formulářích, aplikace se nebude moct podporují více instancí stejného formuláře.  
  
 Pokud vytvoříte aplikaci s podporou více dokumentů nejvyšší úrovně, ploše je implicitní nadřazeného prvku pro dokument a rámec dokumentu není omezen na klientské oblasti aplikace. Můžete otevřít několik instancí dokumentu, každou s vlastním rámce, nabídky a ikonou hlavního panelu. Další instance dokumentu můžete zavřít jednotlivě, ale pokud vyberete `Exit` možnost z **souboru** nabídka počáteční instance, aplikace se zavře všechny instance.  
  
 SDI, MDI a více dokumentů nejvyšší úrovně aplikací jsou na základě všech formulářů a používat architektuře dokument/zobrazení.  
  
 Všechny aplikace na základě dialogové okno, podle definice, jsou na základě formulářů. Dialogové aplikace nepoužívá architektuře dokument/zobrazení, takže se musí spravovat metody vytváření a přístup pro vlastní formuláře.  
  
 Základní třída pro formulářové aplikace je [CFormView](../../mfc/reference/cformview-class.md). Pokud vaše aplikace obsahuje podporu databáze, pak můžete také vybrat libovolnou třídu odvozenou z `CFormView`. Formulář je jakékoliv okno odvozené z `CFormView` nebo z libovolné třídy, která dědí z `CFormView`.  
  
 I když používáte základní třídy, jako [CView](../../mfc/reference/cview-class.md), můžete později provést aplikace na základě formulářů pomocí [přidání třídy knihovny MFC](../../mfc/reference/adding-an-mfc-class.md) odvozené z `CFormView` a kontrolu **Generate DocTemplate prostředky** zaškrtnout políčko [Průvodce třídou MFC](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md).  
  
 Po dokončení se Průvodce otevře projekt, a pokud jste vybrali `CFormView` (nebo třídu, která dědí z `CFormView`) jako základní třída nebo pokud jste vytvořili dialogové aplikace, Visual C++ otevře dialogové okno editor. V tomto okamžiku jste připraveni navrhnout první formulář.  
  
### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>Zahajte proces vytváření formulářů spustitelný soubor knihovny MFC  
  
1.  Postupujte podle pokynů v [vytváření aplikací MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  V Průvodce aplikací MFC [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md) vyberte **Document/view – architektura podporu** zaškrtávací políčko.  
  
3.  Vyberte **jednotlivý dokument**, **více dokumentů**, nebo **více dokumentů nejvyšší úrovně**.  
  
    > [!NOTE]
    >  Pokud jste zvolili SDI, MDI nebo rozhraní více dokumentů nejvyšší úrovně ve výchozím nastavení, `CView` je nastaven jako základní třída pro zobrazení vaší aplikace v [generované třídy](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránce průvodce. Chcete-li vytvořit aplikaci založené na formulářích, je nutné vybrat `CFormView` jako základní třída pro zobrazení aplikace. Všimněte si, že Průvodce neposkytuje podporu tisku pro aplikaci na základě formulářů.  
  
4.  Nastavte další možnosti projektu, který má na dalších stránkách průvodce.  
  
5.  Klikněte na tlačítko **Dokončit** pro vygenerování kostru aplikace.  
  
 Další informace naleznete v tématu:  
  
-   [Odvozené třídy zobrazení](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Alternativy k architektuře dokument/zobrazení](../../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [Volby při návrhu aplikací](../../mfc/application-design-choices.md)  
  
## <a name="see-also"></a>Viz také  
 [MFC – Průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)   
 [Zobrazení formulářů](../../mfc/form-views-mfc.md)   
 [Vytváření aplikací MFC ve stylu Průzkumníka souborů](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)   
 [Vytvoření aplikace MFC ve stylu webového prohlížeče](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

