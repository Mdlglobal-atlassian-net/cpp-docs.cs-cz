---
title: 'MFC – ovládací prvky ActiveX: Přidání další stránky přizpůsobených vlastností'
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 87b71fdddc5b52f66c34cdbcdb234c83616d0850
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160338"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC – ovládací prvky ActiveX: Přidání další stránky přizpůsobených vlastností

Ovládací prvek ActiveX v některých případech bude mít více vlastností než rozumně vejde na jednu stránku vlastností. V takovém případě můžete přidat stránky vlastností do ovládacího prvku ActiveX k zobrazení těchto vlastností.

Tento článek popisuje přidání nové stránky vlastností do ovládacího prvku ActiveX, který už má alespoň jednu stránku vlastností. Další informace o přidání uložených vlastností stránky (písma, obrázek nebo barva), najdete v článku [knihovny MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností](../mfc/mfc-activex-controls-using-stock-property-pages.md).

Následující postupy používají ukázkové rozhraní ovládacího prvku ActiveX vytvořené průvodcem ovládacího prvku ActiveX. Proto jsou jedinečné pro tento příklad názvy tříd a identifikátory.

Další informace o použití stránek vlastností v ovládacím prvku ActiveX najdete v následujících článcích:

- [MFC – ovládací prvky ActiveX: Stránky vlastností](../mfc/mfc-activex-controls-property-pages.md)

- [MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Důrazně doporučujeme tuto novou vlastnost, kterou stránky dodržovat standardní pro stránky vlastností ovládacího prvku ActiveX velikost. Stránky uložených vlastností obrázků a barvu míru 250 × 62 jednotky dialogu (DLU). Na stránce vlastností standardní písmo je 250 x 110 dlu. Výchozí stránky vlastností vytvořené průvodcem ovládací prvek ActiveX používá 250 × 62 DLU standard.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Chcete-li vložit šablonu nové stránky vlastností do projektu

1. Pomocí ovládacího prvku projektu otevřený otevřete zobrazení prostředků v pracovním prostoru projektu.

1. Klikněte pravým tlačítkem v zobrazení prostředků, otevřete místní nabídku a klikněte na tlačítko **přidat prostředek**.

1. Rozbalte **dialogové okno** uzel a vyberte možnost **IDD_OLE_PROPPAGE_SMALL**.

1. Klikněte na tlačítko **nový** bude příslušný materiál přidán do projektu.

1. Vyberte novou šablonu stránky vlastností aktualizovat v okně Vlastnosti.

1. Zadejte novou hodnotu **ID** vlastnost. Tento příklad používá **IDD_PROPPAGE_NEWPAGE**.

1. Klikněte na tlačítko **Uložit** na panelu nástrojů.

### <a name="to-associate-the-new-template-with-a-class"></a>Chcete-li přidružit nové šablony s třídou

1. Otevřete zobrazení tříd.

1. Klikněte pravým tlačítkem v zobrazení tříd a otevřete místní nabídku.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat třídu**.

   Tím se otevře [přidat třídu](../ide/add-class-dialog-box.md) dialogové okno.

1. Dvakrát klikněte **třídy knihovny MFC** šablony.

1. V **název třídy** pole [Průvodce třídami MFC](../mfc/reference/mfc-add-class-wizard.md), zadejte název nové třídy dialogového okna. (V tomto příkladu `CAddtlPropPage`.)

1. Pokud chcete změnit názvy souborů, klikněte na tlačítko **změnit**. Zadejte názvy pro implementaci a hlavičkovými soubory, nebo přijměte výchozí názvy.

1. V **základní třída** vyberte `COlePropertyPage`.

1. V **ID dialogu** vyberte **IDD_PROPPAGE_NEWPAGE**.

9. Klikněte na tlačítko **Dokončit** pro vytvoření třídy.

Ovládacího prvku uživatelům umožnit přístup k této nové stránky vlastností, ovládacího prvku vlastnost ID – makro oddíl stránky (umístěný v souboru implementace ovládacího prvku) proveďte následující změny:

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Všimněte si, že musíte zvýšit druhý parametr BEGIN_PROPPAGEIDS – makro (počet stránek vlastností) od 1 do 2.

Je také nutné upravit soubor implementace ovládacího prvku (. Zahrnout hlavičku souboru CPP) (. H) file nové třídy stránky vlastností.

Dalším krokem zahrnuje vytvoření dvou nových prostředků řetězce, které vám poskytne zadejte název a titulek pro nové stránky vlastností.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>Přidání nové prostředky řetězců do stránky vlastností

1. Pomocí ovládacího prvku projektu otevřený otevřete zobrazení prostředků.

1. Dvakrát klikněte **tabulka řetězců** složku a potom dvakrát klikněte na existující řetězec tabulky prostředků, ke kterému chcete přidat řetězec.

   Tabulka řetězců se otevře v okně.

1. Vyberte prázdný řádek na konec tabulky řetězců a zadejte text nebo caption řetězce: například "Další stránka vlastností."

   Tím se otevře **vlastnosti řetězce** stránka zobrazující **titulek** a **ID** polí. **Titulek** pole obsahuje řetězec, který jste zadali.

1. V **ID** vyberte nebo zadejte ID řetězce. Jakmile skončíte, stiskněte klávesu Enter.

   Tento příklad používá **IDS_SAMPLE_ADDPAGE** zadejte název nové stránky vlastností.

1. Zopakujte kroky 3 a 4 s využitím **IDS_SAMPLE_ADDPPG_CAPTION** pro ID a "Stránka Další vlastnost" pro titulek.

1. V. Soubor CPP nové třídy stránky vlastností (v tomto příkladu `CAddtlPropPage`) změnit `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` tak, aby je předaný odkazem na IDS_SAMPLE_ADDPAGE [afxoleregisterpropertypageclass –](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), jako v následujícím příkladu:

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Upravit konstruktoru `CAddtlPropPage` tak, aby je předán IDS_SAMPLE_ADDPPG_CAPTION `COlePropertyPage` konstruktoru, následujícím způsobem:

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Po provedení potřebné změny znovu sestavit projekt a použít kontejner testu otestovat nové stránky vlastností. Zobrazit [testování vlastností a událostí pomocí testování kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak získat přístup ke kontejneru testů.

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
