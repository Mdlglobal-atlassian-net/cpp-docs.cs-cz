---
title: 'MFC – ovládací prvky ActiveX: Přidání další vlastní stránky vlastností'
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 09d85d69efc4c6cf0bf253099bae78c1e570f8a5
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907378"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC – ovládací prvky ActiveX: Přidání další vlastní stránky vlastností

V některých případech bude mít ovládací prvek ActiveX více vlastností, než se dá rozumně přizpůsobit na jednu stránku vlastností. V takovém případě můžete přidat stránky vlastností do ovládacího prvku ActiveX pro zobrazení těchto vlastností.

Tento článek popisuje přidání nových stránek vlastností do ovládacího prvku ActiveX, který již má alespoň jednu stránku vlastností. Další informace o přidání uložených stránek vlastností (písmo, obrázek nebo barva) naleznete v článku [ovládací prvky ActiveX knihovny MFC: Pomocí uložených stránek](../mfc/mfc-activex-controls-using-stock-property-pages.md)vlastností.

Následující postupy používají ukázkovou architekturu ovládacích prvků ActiveX vytvořenou průvodcem ovládacím prvkem ActiveX. Proto jsou názvy tříd a identifikátory v tomto příkladu jedinečné.

Další informace o použití stránek vlastností v ovládacím prvku ActiveX naleznete v následujících článcích:

- [MFC – ovládací prvky ActiveX: Stránky vlastností](../mfc/mfc-activex-controls-property-pages.md)

- [MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Důrazně doporučujeme, aby se nové stránky vlastností dodržovaly standardem velikosti pro stránky vlastností ovládacího prvku ActiveX. Burzovní obrázek a stránky vlastností barev měření dialogových jednotek 250x62 (DLU). Standardní stránka vlastností Font je 250x110 dlu. Výchozí stránka vlastností vytvořená Průvodcem ovládacím prvkem ActiveX používá standard 250x62 DLU.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Vložení nové šablony stránky vlastností do projektu

1. Otevřete projekt ovládacího prvku a otevřete Prostředky v pracovním prostoru projektu.

1. Kliknutím pravým tlačítkem na Prostředky otevřete místní nabídku a klikněte na **Přidat prostředek**.

1. Rozbalte uzel **dialogového okna** a vyberte **IDD_OLE_PROPPAGE_SMALL**.

1. Kliknutím na **Nový** Přidejte prostředek do svého projektu.

1. Vyberte šablonu stránky nové vlastnosti a aktualizujte okno **vlastnosti** (v **prostředky**).

1. Zadejte novou hodnotu pro vlastnost **ID** . V tomto příkladu se používá **IDD_PROPPAGE_NEWPAGE**.

1. Na panelu nástrojů klikněte na **Uložit** .

### <a name="to-associate-the-new-template-with-a-class"></a>Přidružení nové šablony ke třídě

1. Otevřete Zobrazení tříd.

1. Kliknutím pravým tlačítkem myši na Zobrazení tříd otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a pak klikněte na **Přidat třídu**.

   Tím se otevře dialogové okno [Přidat třídu](../ide/add-class-dialog-box.md) .

1. Dvakrát klikněte na šablonu **třídy MFC** .

1. Do pole **název třídy** v [Průvodci třídou MFC](../mfc/reference/mfc-add-class-wizard.md)zadejte název nové třídy dialogového okna. (V tomto příkladu `CAddtlPropPage`.)

1. Chcete-li změnit názvy souborů, klikněte na tlačítko **změnit**. Zadejte názvy pro vaši implementaci a hlavičkové soubory nebo přijměte výchozí názvy.

1. V poli **základní třída** vyberte `COlePropertyPage`.

1. V poli **ID dialogového okna** vyberte možnost **IDD_PROPPAGE_NEWPAGE**.

9. Kliknutím na tlačítko **Dokončit** vytvořte třídu.

Chcete-li umožnit uživatelům ovládacího prvku přístup k této nové stránce vlastností, proveďte následující změny v oddílu makra ID stránky vlastností ovládacího prvku (nachází se v souboru implementace ovládacího prvku):

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Všimněte si, že je nutné zvětšit druhý parametr makra BEGIN_PROPPAGEIDS (počet stránek vlastností) od 1 do 2.

Je také nutné upravit implementační soubor ovládacího prvku (. CPP), aby zahrnoval hlavičku (. H) souboru nové třídy stránky vlastností.

Další krok zahrnuje vytvoření dvou nových prostředků řetězce, které budou poskytovat název typu a titulek pro novou stránku vlastností.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>Přidání nových prostředků řetězce na stránku vlastností

1. Otevřete projekt ovládacího prvku a otevřete Prostředky.

1. Dvakrát klikněte na složku **tabulka řetězců** a pak dvakrát klikněte na existující prostředek tabulky řetězců, ke kterému chcete přidat řetězec.

   Tím se otevře tabulka řetězců v okně.

1. Na konci tabulky řetězců vyberte prázdný řádek a zadejte text nebo titulek řetězce: například "Další stránka vlastností".

   Otevře se stránka s **vlastnostmi řetězce** zobrazující pole **titulků** a **ID** . Pole **Titulek** obsahuje řetězec, který jste zadali.

1. V poli **ID** vyberte nebo zadejte ID pro řetězec. Po dokončení stiskněte klávesu ENTER.

   V tomto příkladu se pro název typu nové stránky vlastností používá **IDS_SAMPLE_ADDPAGE** .

1. Opakujte kroky 3 a 4 pomocí **IDS_SAMPLE_ADDPPG_CAPTION** pro ID a další stránku vlastností pro titulek.

1. V. Soubor cpp vaší nové třídy stránky vlastností (v tomto příkladu `CAddtlPropPage`) `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` upravte tak, aby IDS_SAMPLE_ADDPAGE byla předána pomocí [AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), jak je uvedeno v následujícím příkladu:

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Upravte konstruktor pro `CAddtlPropPage` tak, aby byl `COlePropertyPage` do konstruktoru předán IDS_SAMPLE_ADDPPG_CAPTION následujícím způsobem:

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Po provedení nezbytných úprav znovu sestavte projekt a pomocí kontejneru testu otestujte novou stránku vlastností. Informace o tom, jak získat přístup ke kontejneru testu, naleznete v tématu [Testování vlastností a událostí pomocí kontejneru testů](../mfc/testing-properties-and-events-with-test-container.md) .

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
