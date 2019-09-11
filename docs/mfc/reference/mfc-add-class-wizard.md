---
title: Průvodce přidáním třídy MFC
ms.date: 09/06/2019
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: 2c82e084de2123c579299ca6490bdfcfdac5d255
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908008"
---
# <a name="mfc-add-class-wizard"></a>Průvodce přidáním třídy MFC

Pomocí tohoto průvodce kódem můžete přidat třídu do existujícího projektu knihovny MFC nebo přidat třídu do projektu ATL, který podporuje knihovnu MFC. Třídy knihovny MFC můžete také přidat do projektů Win32, které mají podporu knihovny MFC. Funkce, které jste zadali při vytváření projektu, určují možnosti, které jsou k dispozici v tomto dialogovém okně. Chcete-li získat přístup k průvodci, klikněte na tlačítko **Přidat třídu** v [Průvodci třídou](mfc-class-wizard.md).

![Průvodce přidáním třídy MFC](media/add-mfc-class-wizard.png "Průvodce přidáním třídy MFC")

## <a name="names"></a>Názvy

Na této stránce zadejte název třídy, základní třídu a názvy souborů pro novou třídu.

- **Název třídy**

  Určuje název nové třídy a poskytuje výchozí základ pro názvy ID a soubory na této stránce. C++třídy obvykle začínají řetězcem "C", takže například "CMyClass" bude "MyClass. h" atd.

- **Základní třída**

  Určuje název základní třídy pro novou třídu. Ve výchozím nastavení je základní třídou [CWnd](../../mfc/reference/cwnd-class.md). Základní třída, kterou vyberete, určuje, zda jsou ostatní pole na této stránce aktivní.

  Typ třídy, kterou nastavíte jako základní třídu určuje, zda má třída ID dialogového okna nebo ID prostředku. Obecné typy tříd jsou následující:

  - Třídy jako [CButton](../../mfc/reference/cbutton-class.md), [CWnd](../../mfc/reference/cwnd-class.md)nebo [objektu CDOCUMENT](../../mfc/reference/cdocument-class.md), které nevyžadují ID dialogu nebo ID prostředku. Tyto třídy nepoužívají dialog nebo ID prostředku. Pokud pro základní třídu vyberete jednu z těchto tříd, pole **ID dialogového okna** a **ID prostředku DHTML** budou neaktivní.

  - Třídy jako [CDialog](../../mfc/reference/cdialog-class.md), [CFormView](../../mfc/reference/cformview-class.md)nebo [CPropertyPage –](../../mfc/reference/cpropertypage-class.md), které vyžadují ID dialogu.

  - Třída [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md), která vyžaduje ID dialogu, ID prostředku DHTML a název souboru HTML.

  Pro třídy, které vyžadují ID dialogu, může být efektivnější použít [Editor prostředků](../../windows/resource-editors.md) k vytvoření prostředku dialogového okna, přiřazení jeho ID v [Průvodci třídou](mfc-class-wizard.md)a následné vytvoření třídy přidružené k tomuto ID prostředku. Další informace o vytvoření standardního dialogového okna systému Windows naleznete v tématu [Vytvoření nového dialogového okna](../../windows/creating-a-new-dialog-box.md) .

  > [!NOTE]
  > Pokud nejprve vytvoříte prostředek dialogového okna a odvodíte jeho novou třídu z `CDHtmlDialog`, odstraňte standardní tlačítka Windows **OK** a **Storno** , která se zobrazí v dialogovém okně výchozí. Standardní dialogové okno systému Windows je hostitelem formuláře DHTML, který obsahuje vlastní tlačítka **OK** a **Storno** .

  I když vaše dialogové okno může obsahovat ovládací prvky Windows i ovládací prvky DHTML, nedoporučuje se.

- **ID dialogu**

  Určuje ID dialogového okna, `CDialog`Pokud jste vybrali, `CFormView`, `CPropertyPage`nebo `CDHtmlDialog` jako **základní třídu**.

- **soubor. h**

  Nastaví název hlavičkového souboru pro novou třídu objektu. Ve výchozím nastavení je tento název založen na názvu, který zadáte v **názvu třídy**. Kliknutím na tlačítko se třemi tečkami uložte název souboru do zvoleného umístění nebo přidejte deklaraci třídy do existujícího souboru. Pokud zvolíte existující soubor, průvodce ho nebude ukládat do vybraného umístění, dokud v průvodci nekliknete na **Dokončit** .

  Průvodce nepřepisuje soubor. Pokud vyberete název existujícího souboru, po kliknutí na tlačítko **Dokončit**vás průvodce vyzve, abyste označili, zda má být deklarace třídy připojena k obsahu souboru. Kliknutím na **Ano** přidejte soubor. Kliknutím na **ne** se vrátíte do průvodce a zadáte jiný název souboru.

- **soubor. cpp**

  Nastaví název implementačního souboru pro třídu nového objektu. Ve výchozím nastavení je tento název založen na názvu, který zadáte v **názvu třídy**. Kliknutím na tlačítko se třemi tečkami uložte název souboru do zvoleného umístění. Soubor není uložen do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.

  Průvodce nepřepisuje soubor. Pokud vyberete název existujícího souboru, po kliknutí na tlačítko **Dokončit**vás průvodce vyzve, abyste označili, zda by měla být implementace třídy připojena k obsahu souboru. Kliknutím na **Ano** přidejte soubor. Kliknutím na **ne** se vrátíte do průvodce a zadáte jiný název souboru.

- **Aktivní přístupnost**

  Povolí podporu aktivního usnadnění knihovny MFC voláním [EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) v konstruktoru. Tato možnost je k dispozici pro třídy odvozené od [CWnd](../../mfc/reference/cwnd-class.md).

- **Automatizace**

  Nastaví na úrovni třídy podporu pro [automatizaci](../../mfc/automation.md). Automatizace na úrovni třídy je k dispozici pro všechny třídy, které podporují automatizaci. Je k dispozici také pro projekty vytvořené s podporou pro automatizaci. To znamená, že buď projekt knihovny MFC, který [podporuje ATL](../../atl/reference/mfc-support-in-atl-projects.md), nebo projekt knihovny MFC, pro který jste zaškrtli políčko **Automatizace** , na stránce [Pokročilé funkce](../../mfc/reference/advanced-features-mfc-application-wizard.md) v Průvodci aplikací knihovny MFC.

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

## <a name="see-also"></a>Viz také:

[MFC – třída](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)
