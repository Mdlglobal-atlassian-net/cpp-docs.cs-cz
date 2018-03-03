---
title: "Přidání funkce pomocí průvodců kódem (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.classes
dev_langs:
- C++
helpviewer_keywords:
- code wizards [C++]
- wizards [C++], code
- Visual C++ projects, adding functionality
- projects [C++], adding functionality
- class wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c27aeb10a58c828b6503ce96ddaadf138c258f27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-functionality-with-code-wizards-c"></a>Přidání funkce pomocí průvodců kódem (C++)
Po vytvoření projektu, můžete změnit nebo přidat do tohoto projektu funkce. Například vytvářet nové třídy, přidávat nové členské funkce a proměnné a přidání automatizace metody a vlastnosti. Průvodci kódem jsou navržené tak, abyste mohli provádět tyto akce.  
  
> [!NOTE]
>  Teď můžete přidat obslužné rutiny zpráv a mapování jejich a přepsat virtuální funkce MFC pomocí [vlastnosti – okno](/visualstudio/ide/reference/properties-window).  
  
## <a name="accessing-visual-c-code-wizards"></a>Přístup k Průvodci kódem jazyka Visual C++  
 Existují tři umístění, kde může získat přístup k Průvodci kódem Visual C++:  
  
-   Na **projektu** nabídce **přidat novou položku** příkaz umožňuje zprovoznit `Add New Item` dialogové okno, které vám pomůžou při přidávání nové soubory do projektu. **Přidat třídu** příkaz zobrazí [přidat třídu](../ide/add-class-dialog-box.md) dialogové okno, která zase otevřít průvodců pro všechny třídy typy je můžete přidat do projektu. **Přidat prostředek** příkaz zobrazí [přidat prostředek](../windows/add-resource-dialog-box.md) dialogové okno, ve kterém můžete vytvořit nebo vybrat prostředek pro přidání do projektu.  
  
     Pokud zvýraznění třídy nebo rozhraní ve vašem projektu v zobrazení tříd **projektu** nabídka zobrazí následující příkazy:  
  
    -   **Implementovat rozhraní** (z ovládacího prvku třídy pouze)  
  
    -   **Add – funkce**  
  
    -   **Přidání proměnné**  
  
    -   **Přidat připojení bod** (pouze třída ATL)  
  
    -   **Přidejte metodu** (z rozhraní pouze)  
  
    -   **Přidat vlastnost** (z rozhraní pouze)  
  
    -   **Přidat událost** (z ovládacího prvku třídy pouze)  
  
-   V **Průzkumníku řešení**, kliknete pravým tlačítkem na libovolné složky a kliknutím na **přidat** nabídky pomocí zástupce umožňuje přidat nové nebo existující soubory, další složky, položky, třídy, prostředky a webových odkazů na projekt.  
  
-   Z [okno Zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), pravým tlačítkem myši na příslušný uzel a kliknutím na **přidat** nabídky pomocí zástupce umožňuje přidat funkce, proměnné, třídy, vlastnosti, metody, události, rozhraní, body připojení nebo jiný kód do projektu.  
  
    > [!NOTE]
    >  Visual Studio neposkytuje průvodce přidat rozhraní do projektu. Můžete přidat do projektu knihovny ATL nebo na rozhraní [přidání podpory knihovny ATL do projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) přidáním jednoduchého objektu pomocí [ATL Simple Object Wizard](../atl/reference/atl-simple-object-wizard.md). Můžete také otevřít souboru projektu a vytvořit rozhraní zadáním:  
  
    ```  
    interface IMyInterface {  
    };  
  
    ```  
  
     V tématu [implementace rozhraní](../ide/implementing-an-interface-visual-cpp.md) a [přidávání objektů a ovládacích prvků do projektu knihovny ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) Další informace.  
  
    |Přístupový kód průvodce|Popis|  
    |-----------------------------|-----------------|  
    |Přidat novou položku|Průvodci kódem přidat novou položku do projektu přidejte zdrojové soubory. V případě potřeby další adresáře jsou vytvořeny tak, aby obsahovala soubory, které modul sestavení projektu je očekává. Průvodci kódem, které jsou dostupné na ikonu Přidat položku patří:<br /><br /> -Přidáte C++ zdrojové soubory (sada, .h, .idl, .rc, SRF, .def, .rgs).<br />-Přidáte soubory vývojového webové (.html, .asp, .css, .xml).<br />-Přidáte soubory nástrojů a prostředků (.bmp, .cur, .ico, který, .rct, .sql, .txt).<br /><br /> Tito průvodci kódem obecně nepožadují žádné informace, ale přidá soubor do vašeho vývojového stromu. Může přejmenujte soubor v okně Vlastnosti.|  
    |Průzkumník řešení|Průvodci kódem, který je k dispozici v Průzkumníku řešení závisí na umístění kurzoru po kliknete pravým tlačítkem na položku. Pokud **přidat** možnost se nezobrazí, klikněte pravým tlačítkem na položku, přesuňte kurzor jednu úroveň ve stromové struktuře vývoj a zkuste to znovu. Průvodci kódem vždy umístí další kód na příslušné místo ve vývojovém stromu, bez ohledu kde je kurzor. Průvodci kódem, které jsou k dispozici v Průzkumníku řešení patří:<br /><br /> -Přidejte třídu (otevře **přidat třídu** dialogové okno obsahuje Průvodce kódem).<br />-Přidat prostředek (nový, importovat nebo vlastní).<br />-Přidáte odkaz na Web.|  
    |zobrazení tříd|Průvodci kódem, který je k dispozici v zobrazení tříd závisí na umístění kurzoru po pravým tlačítkem na položku. Pokud **přidat** možnost se nezobrazí, pravým tlačítkem na položku, přesuňte kurzor jednu úroveň ve stromu tříd a zkuste to znovu. Průvodci kódem vždy umístí další kód na příslušné místo ve vývojovém stromu, bez ohledu kde je kurzor. Průvodci kódem k dispozici prostřednictvím třídy zobrazení patří:<br /><br /> -   [Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md).<br />-   [Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md).<br />-   [Přidání třídy](../ide/adding-a-class-visual-cpp.md).<br />-   [Implementovat rozhraní](../ide/implement-interface-wizard.md) (z ovládacího prvku třídy pouze)<br />-   [Přidat připojení bod](../ide/implement-connection-point-wizard.md) (pouze třída ATL)<br />-   [Přidejte metodu](../ide/add-method-wizard.md) (z rozhraní pouze)<br />-   [Přidat vlastnost](../ide/names-add-property-wizard.md) (z rozhraní pouze)<br />-   [Přidat událost](../ide/add-event-wizard.md) (z ovládacího prvku třídy pouze)<br /><br /> Otevře se výběr přidat třídu **přidat třídu** dialogové okno, která umožňuje přístup na všechny přidat třídu Průvodce kódem.|  
  
## <a name="see-also"></a>Viz také  
 [Přepisování virtuální funkce](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Navigace strukturou třídy](../ide/navigating-the-class-structure-visual-cpp.md)   
 [Tvorba běžných projektů pomocí průvodců aplikací](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Typy projektů Visual C++](../ide/visual-cpp-project-types.md)   
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)