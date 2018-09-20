---
title: Průvodce přidáním třídy MFC | Dokumentace Microsoftu
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
ms.openlocfilehash: 0f9098bf7aa812e79e0928266d52ad2c1602135c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419841"
---
# <a name="mfc-add-class-wizard"></a>Průvodce přidáním třídy MFC

Pomocí tohoto kódu průvodce Přidat třídu do existujícího projektu knihovny MFC nebo přidání třídy do projektu ATL, který podporuje knihovnu MFC. Můžete také přidat třídy knihovny MFC pro projekty Win32, které mají podporu knihovny MFC. Funkce, které jste zadali při vytváření projektu určete možnosti dostupné v tomto dialogovém.

## <a name="names"></a>Názvy

Na této stránce zadejte název třídy, základní třídy a názvy souborů pro novou třídu.

- **Název třídy**

   Určuje název nové třídy a poskytuje výchozí základ pro názvy identifikátorů a souborů na této stránce. Třídy jazyka C++ se obvykle začínáte s "C", tedy například "CMyClass" stane "MyClass.h", a tak dále.

- **Základní třída**

   Určuje název základní třídy pro novou třídu. Ve výchozím nastavení, základní třída je [CWnd](../../mfc/reference/cwnd-class.md). Základní třídy, které jste vybrali Určuje, zda ostatní pole na této stránce jsou aktivní.

   Typ třídy, které jste nastavili jako základní třída určuje, zda třída má dialogové okno ID nebo ID prostředku. Obecné typy tříd jsou následující:

   - Třídy, jako například [CButton](../../mfc/reference/cbutton-class.md), [CWnd](../../mfc/reference/cwnd-class.md), nebo [CDocument](../../mfc/reference/cdocument-class.md), které nevyžadují dialogové okno s ID nebo ID prostředku. Tyto třídy nepoužívejte ID dialogové okno nebo prostředků. Pokud vyberete jednu z těchto tříd pro základní třídu, **ID dialogu** pole a **ID prostředku DHTML** pole jsou neaktivní.

   - Třídy, jako například [CDialog](../../mfc/reference/cdialog-class.md), [CFormView](../../mfc/reference/cformview-class.md), nebo [CPropertyPage](../../mfc/reference/cpropertypage-class.md), které vyžadují identifikátor dialogového okna.

   - Třída [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md), což vyžaduje ID dialogu, ID prostředku DHTML a název souboru HTML.

   Pro třídy, které vyžadují ID dialogu, může pro vás výhodnější používat [editor prostředků](../../windows/resource-editors.md) k vytvoření prostředku dialogového okna, přiřaďte jeho ID v [okno vlastností](/visualstudio/ide/reference/properties-window)a poté vytvoříte třídu související Pomocí tohoto ID prostředku. Zobrazit [vytváření nového dialogového okna](../../windows/creating-a-new-dialog-box.md) Další informace o vytvoření standardního dialogového okna Windows.

   > [!NOTE]
   > Pokud nejprve vytvoříte prostředek dialogového okna a odvodit svou novou třídu `CDHtmlDialog`, odstranit standardní Windows **OK** a **zrušit** tlačítka, která se zobrazí v dialogovém okně výchozí. Standardní dialogové okno Windows hostuje DHTML formuláře, který obsahuje vlastní **OK** a **zrušit** tlačítka.

   Při vašem dialogovém okně mohou obsahovat ovládací prvky Windows a ovládací prvky jazyka DHTML, se nedoporučuje.

- **ID dialogu**

   Určuje ID dialogu, pokud jste vybrali `CDialog`, `CFormView`, `CPropertyPage`, nebo `CDHtmlDialog` jako **základní třída**.

- **soubor .h**

   Nastaví název hlavičkového souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu je zadat v **název třídy**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby, nebo připojit k existujícímu souboru deklaraci třídy. Pokud zvolíte existující soubor, Průvodce neuloží se do vybraného umístění dokud kliknutím **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda by měla být k obsah souboru připojen deklaraci třídy. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **soubor .cpp**

   Nastaví název implementačního souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu je zadat v **název třídy**. Klikněte na tlačítko se třemi tečkami se uložit název souboru do umístění podle vašeho výběru. Soubor se neukládá do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda má být připojen implementace třídy do obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **Active accessibility**

   Umožňuje podporu knihovny MFC Active Accessibility voláním [EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) v konstruktoru. Tato možnost je dostupná pro třídy odvozené z [CWnd](../../mfc/reference/cwnd-class.md).

- **ID prostředku DHTML**

   Platí pro třídy odvozené od `CDHtmlDialog` pouze. Určuje Identifikátor prostředku dialogového okna DHTML. ID prostředku se zobrazí v části HTML souboru .rc v projektu, spolu s názvem souboru dialogové okno pole HTML. DHTML prostředků, pomocí tohoto ID se hostuje dialogovém okně identifikovaný **ID dialogu**.

- **. Soubor HTM**

   Platí pro třídy odvozené od `CDHtmlDialog` pouze. Nastaví název souboru ve formátu HTML pro dialogové okno Dynamic HTML. Ve výchozím nastavení tento název souboru je podle názvu třídy. Název souboru se zobrazí v části HTML souboru .rc v projektu, spolu s ID DHTML dialog box prostředku.

- **Automatizace**

   Nastaví úroveň třídy podpory pro [automatizace](../../mfc/automation.md). Automation na úrovni třídy je k dispozici pro všechny třídy, které podporují služby Automation. Je také k dispozici pro projekty vytvořené pomocí podpory pro automatizaci. To znamená, že projekt knihovny MFC [podporuje ATL](../../atl/reference/mfc-support-in-atl-projects.md), nebo projektu knihovny MFC, pro kterou jste vybrali **automatizace** zaškrtávací políčko [rozšířené funkce](../../mfc/reference/advanced-features-mfc-application-wizard.md) stránce knihovny MFC Průvodce aplikací.

   |Možnost|Popis|
   |------------|-----------------|
   |**None**|Označuje, že třída nemá žádné podporu automatizace.|
   |**Automatizace**|Označuje, že třída podporuje služby Automation. Pokud vyberete tuto možnost, nově vytvořené třídy je k dispozici jako programovatelný objekt automatizace klientskými aplikacemi, jako je například Microsoft Visual Basic a aplikaci Microsoft Excel. Tato možnost není k dispozici pro základní třídy uvedeny za touto tabulkou.|
   |**Vytvořitelný modelem ID typu**|Označuje, že třídu a projekt podporovat jiné aplikace, vytváření objektů této třídy pomocí automatizace. Pomocí této možnosti můžete klientům automatizace přímo vytvořit automatizační objekt. Typ Identifikátoru v textovém poli používá klientská aplikace zadat objekt, který má být vytvořen; je v celém systému a musí být jedinečný. Tato možnost není k dispozici pro základní třídy uvedeny za touto tabulkou.|

   Podpora automatizace není k dispozici pro následující základní třídy:

   - `CAsyncMonitorFile`

   - `CAsyncSocket`

   - `CCachedDataPathProperty`

   - `CConnectionPoint`

   - `CDatabase`

   - `CDataPathProperty`

   - `CHttpFilter`

   - `CHttpServer`

   - `CInternetSession`

   - `CObject`

   - `CSocket`

- **ID typu**

   Nastaví ID typu třídy. **ID typu** zřetězí název projektu a název nové třídy následujícím způsobem: *MFCProj.MFCClass*. Toto ID lze změnit pouze v případě, že jste vybrali **automatizace** možnost **Vytvořitelné podle ID typu**.

- **Generování DocTemplate prostředků**

   Indikuje, že dokumenty, které vytvořila aplikace prostředků šablony dokumentu. Pokud chcete aktivovat toto zaškrtávací políčko, projektu musí podporovat architekturu document/view knihovny MFC a musí být základní třídy této třídy [CFormView](../../mfc/reference/cformview-class.md).

   Zobrazit [šablony dokumentů a proces vytváření dokumentů/zobrazení](../../mfc/document-templates-and-the-document-view-creation-process.md) Další informace.

## <a name="see-also"></a>Viz také

[Třída knihovny MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)
