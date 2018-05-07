---
title: Průvodce přidáním třídy MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9560dec12a7710076f752d5329269c844f0d3a8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-add-class-wizard"></a>Průvodce přidáním třídy MFC
Pomocí tohoto průvodce kód přidejte třídu do existujícího projektu knihovny MFC nebo přidejte třídu do projektu knihovny ATL, který podporuje MFC. MFC – třídy můžete také přidat do Win32 projektů, které mají Podpora MFC. Funkce, které jste zadali při vytváření projektu určete možnosti k dispozici v tomto dialogovém.  
  
## <a name="names"></a>Názvy  
 Na této stránce zadejte název třídy, základní třídy a názvy souborů pro novou třídu.  
  
 **Název třídy**  
 Určuje název nové třídy a poskytuje výchozí základ pro názvy ID a souborů na této stránce. Třídy C++ "C", obvykle začínat, takže například "CMyClass" bude "MyClass.h", a tak dále.  
  
 **Base – třída**  
 Určuje název základní třídy pro novou třídu. Ve výchozím nastavení, je základní třída [CWnd](../../mfc/reference/cwnd-class.md). Základní třídy, kterou vyberete určí, zda jsou ostatní pole na této stránce aktivní.  
  
 Typ třídy, které nastavíte jako základní třída určuje, zda má třída Identifikátor dialogového okna nebo prostředku. Obecné typy třídy jsou následující:  
  
-   Třídy, jako [CButton](../../mfc/reference/cbutton-class.md), [CWnd](../../mfc/reference/cwnd-class.md), nebo [CDocument](../../mfc/reference/cdocument-class.md), které nevyžadují dialogové okno ID nebo ID prostředku. Tyto třídy nepoužívejte dialogové okno nebo prostředků. Pokud vyberete jednu z těchto tříd pro základní třídu, **dialogové okno ID** pole a **ID prostředku DHTML** pole jsou neaktivní.  
  
-   Třídy, jako [CDialog](../../mfc/reference/cdialog-class.md), [CFormView](../../mfc/reference/cformview-class.md), nebo [CPropertyPage](../../mfc/reference/cpropertypage-class.md), které vyžadují identifikátor dialogového okna.  
  
-   Třída [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md), což vyžaduje, aby Identifikátor dialogového okna, ID prostředku DHTML a název souboru HTML.  
  
 Pro třídy vyžadující Identifikátor dialogového okna, může pro vás efektivnější použít [editor prostředků](../../windows/resource-editors.md) k vytvoření prostředku dialogového okna, přiřazení jeho ID v [vlastnosti – okno](/visualstudio/ide/reference/properties-window)a poté vytvořit související třídy s ID tohoto zdroje. V tématu [vytvoření nového dialogového okna](../../windows/creating-a-new-dialog-box.md) Další informace o vytváření standardní dialogové okno systému Windows.  
  
> [!NOTE]
>  Pokud nejprve vytvořte zdroj dialogového okna a odvodíte jeho novou třídu z `CDHtmlDialog`, odstranit standardní Windows **OK** a **zrušit** tlačítek v dialogovém okně výchozí. Standardní dialogové okno hostitelem DHTML formuláře, který obsahuje vlastní **OK** a **zrušit** tlačítka.  
  
 Při vašem dialogovém okně může obsahovat ovládací prvky Windows a ovládací prvky jazyka DHTML se nedoporučuje.  
  
 **Identifikátor dialogového okna**  
 Určuje ID dialogového okna, pokud jste vybrali `CDialog`, `CFormView`, `CPropertyPage`, nebo `CDHtmlDialog` jako **základní třída**.  
  
 **soubor h**  
 Nastaví název hlavičky souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu poskytují v **název třídy**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby nebo připojit k existující soubor deklaraci třídy. Pokud zvolíte existující soubor, průvodce jej neuloží do vybraného umístění dokud klikněte na tlačítko **Dokončit** v průvodci.  
  
 Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být deklaraci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.  
  
 **souboru**  
 Nastaví název souboru implementace pro nový objekt třídu. Ve výchozím nastavení, tento název je založen na názvu poskytují v **název třídy**. Klikněte na tlačítko se třemi tečkami uložíte soubor do umístění podle vaší volby. Soubor se neuloží do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.  
  
 Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být implementaci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.  
  
 **Active accessibility**  
 Povolí podporu MFC pro Active Accessibility voláním [EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) v konstruktoru. Tato možnost je dostupná pro třídy odvozené od [CWnd](../../mfc/reference/cwnd-class.md).  
  
 **ID prostředku DHTML**  
 Platí pro třídy odvozené od třídy `CDHtmlDialog` pouze. Určuje ID prostředku dialogového okna DHTML. ID prostředku se zobrazí v části projektu projektového souboru název souboru HTML dialogové okno pole HTML. Prostředek DHTML identifikovanou pomocí tohoto ID se hostuje na dialogovém okně identifikovaný **Identifikátor dialogového okna**.  
  
 **. Soubor HTM**  
 Platí pro třídy odvozené od třídy `CDHtmlDialog` pouze. Nastaví název souboru ve formátu HTML pro dialogové okno DHTML. Ve výchozím nastavení je tento název souboru založen na název třídy. Název souboru se zobrazí v části HTML .rc souboru projektu, společně s ID jazyka DHTML dialogové okno pole prostředku.  
  
 **Automatizace**  
 Nastaví úroveň třída podpory pro [automatizace](../../mfc/automation.md). Automatizace na úrovni třídy je k dispozici pro všechny třídy, které podporují automatizace. Je k dispozici pro projekty vytvořené s podporou pro automatizaci. To znamená, že projekt knihovny MFC [podporuje ATL](../../atl/reference/mfc-support-in-atl-projects.md), nebo projektu knihovny MFC, pro který jste vybrali **automatizace** zaškrtávací políčko [upřesňující funkce](../../mfc/reference/advanced-features-mfc-application-wizard.md) stránky MFC Průvodce vytvořením aplikace.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**None**|Označuje, že má třída nepodporuje automatizaci.|  
|**Automatizace**|Označuje, že třída podporuje automatizace. Pokud vyberete tuto možnost, nově vytvořený třída je k dispozici jako programovatelný objekt automatizace klientskými aplikacemi, jako je například Microsoft Visual Basic a aplikaci Microsoft Excel. Tato možnost není k dispozici pro základní třídy uvedené za touto tabulkou.|  
|**Vytvořitelné podle typu Identifikátoru**|Označuje, že třída i projekt podporu dalších aplikací, vytváření objektů této třídy pomocí automatizace. Pomocí této možnosti mohou klienti automatizace přímo vytvářet objekt automatizace. ID typu v textovém poli klientskou aplikací slouží k určení objekt, který má být vytvořen; To je v systému a musí být jedinečný. Tato možnost není k dispozici pro základní třídy uvedené za touto tabulkou.|  
  
 Podpora automatizace není k dispozici pro následující základní třídy:  
  
-   `CAsyncMonitorFile`  
  
-   `CAsyncSocket`  
  
-   `CCachedDataPathProperty`  
  
-   `CConnectionPoint`  
  
-   `CDatabase`  
  
-   `CDataPathProperty`  
  
-   `CHttpFilter`  
  
-   `CHttpServer`  
  
-   `CInternetSession`  
  
-   `CObject`  
  
-   `CSocket`  
  
 **ID typu**  
 Nastaví ID typu třídy. **ID typu** zřetězí název projektu a název nové třídy následujícím způsobem: *MFCProj.MFCClass*. Tento Identifikátor je možné změnit pouze v případě, že jste vybrali **automatizace** možnost **Vytvořitelné podle ID typu**.  
  
 **Generovat prostředky DocTemplate**  
 Znamená, že dokumenty, které vytvořila aplikace mají prostředky šablony dokumentu. Pokud chcete aktivovat toto políčko, musí podporovat projektu knihovny MFC document/view – architektura a musí být základní třídě této třídy [CFormView](../../mfc/reference/cformview-class.md).  
  
 V tématu [šablony dokumentů a proces tvorby Document/View –](../../mfc/document-templates-and-the-document-view-creation-process.md) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Třída knihovny MFC](../../mfc/reference/adding-an-mfc-class.md)   
 [Přidání třídy](../../ide/adding-a-class-visual-cpp.md)
