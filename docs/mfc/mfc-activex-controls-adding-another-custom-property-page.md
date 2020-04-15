---
title: 'MFC – ovládací prvky ActiveX: Přidání další stránky přizpůsobených vlastností'
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 02c87c2c5283b7293c2a7ab028ec9a2abbba2b33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364742"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC – ovládací prvky ActiveX: Přidání další stránky přizpůsobených vlastností

V některých případě ovládací prvek ActiveX bude mít více vlastností, než se může přiměřeně vejít na jednu stránku vlastností. V takovém případě můžete přidat stránky vlastností do ovládacího prvku ActiveX a zobrazit tyto vlastnosti.

Tento článek popisuje přidání nových stránek vlastností do ovládacího prvku ActiveX, který již obsahuje alespoň jednu stránku vlastností. Další informace o přidávání stránek vlastností akcií (písmo, obrázek nebo barva) naleznete v článku [Ovládací prvky ActiveX knihovny MFC: Použití stránek vlastností skladových zásob](../mfc/mfc-activex-controls-using-stock-property-pages.md).

Následující postupy používají ukázkovou architekturu ovládacího prvku ActiveX vytvořenou Průvodcem ovládacím prvkem ActiveX. Proto názvy tříd a identifikátory jsou jedinečné v tomto příkladu.

Další informace o použití stránek vlastností v ovládacím prvku ActiveX naleznete v následujících článcích:

- [MFC – ovládací prvky ActiveX: Stránky vlastností](../mfc/mfc-activex-controls-property-pages.md)

- [MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Důrazně doporučujeme, aby nové stránky vlastností dodržovaly standard velikosti pro stránky vlastností ovládacího prvku ActiveX. Stránky vlastností stock obrázku a barvy měří 250x62 dialogových jednotek (DLU). Standardní stránka vlastnosti písma je 250x110 DL. Výchozí stránka vlastností vytvořená Průvodcem ovládacím prvkem ActiveX používá standard 250x62 DLU.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Vložení nové šablony stránky vlastností do projektu

1. S otevřeným řídicím projektem otevřete zobrazení zdrojů v pracovním prostoru projektu.

1. Klepnutím pravým tlačítkem myši v okně Zobrazení prostředků otevřete místní nabídku a klepněte na příkaz **Přidat zdroj**.

1. Rozbalte uzel **dialoga** a vyberte **IDD_OLE_PROPPAGE_SMALL**.

1. Chcete-li zdroj přidat do projektu, klepněte na **tlačítko Nový.**

1. Vyberte novou šablonu stránky vlastností, chcete-li aktualizovat okno **Vlastnosti** (v **zobrazení prostředků).**

1. Zadejte novou hodnotu vlastnosti **ID.** Tento příklad používá **IDD_PROPPAGE_NEWPAGE**.

1. Na panelu nástrojů klikněte na tlačítko **Uložit**.

### <a name="to-associate-the-new-template-with-a-class"></a>Přidružení nové šablony ke třídě

1. Otevřete zobrazení tříd.

1. Klepnutím pravým tlačítkem myši v zobrazení tříd otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat třídu**.

   Otevře se dialogové okno [Přidat třídu.](../ide/add-class-dialog-box.md)

1. Poklepejte na šablonu **třídy knihovny MFC.**

1. Do pole **Název třídy** v [Průvodci třídou knihovny MFC](../mfc/reference/mfc-add-class-wizard.md)zadejte název nové třídy dialogu. (V tomto `CAddtlPropPage`příkladu .)

1. Pokud chcete změnit názvy souborů, klepněte na **tlačítko Změnit**. Zadejte názvy implementačních souborů a souborů hlaviček nebo přijměte výchozí názvy.

1. V poli **Základní** třída `COlePropertyPage`vyberte .

1. V **dialogovém okně ID** vyberte **IDD_PROPPAGE_NEWPAGE**.

1. Chcete-li vytvořit třídu, klepněte na **tlačítko Dokončit.**

Chcete-li uživatelům ovládacího prvku povolit přístup k této nové stránce vlastností, proveďte následující změny v části maker ID stránky vlastností ovládacího prvku (umístěné v souboru implementace ovládacího prvku):

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Všimněte si, že je nutné zvýšit druhý parametr BEGIN_PROPPAGEIDS makro (počet stránek vlastností) z 1 na 2.

Je také nutné upravit soubor implementace ovládacího prvku (. CPP) tak, aby obsahoval záhlaví (. H) soubor nové třídy stránky vlastností.

Dalším krokem je vytvoření dvou nových prostředků řetězce, které budou poskytovat název typu a titulek pro novou stránku vlastností.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>Přidání nových prostředků řetězce na stránku vlastností

1. S otevřeným řídicím projektem otevřete zobrazení zdrojů.

1. Poklepejte na složku **Tabulka řetězců** a potom poklepejte na existující prostředek tabulky řetězců, do kterého chcete přidat řetězec.

   Otevře se tabulka řetězců v okně.

1. Vyberte prázdný řádek na konci tabulky řetězců a zadejte text nebo titulek řetězce: například "Stránka další vlastnosti".

   Otevře se stránka **Vlastnosti řetězce** s poli **Titulek** a **ID.** Pole **Titulek** obsahuje zadaný řetězec.

1. Do pole **ID** vyberte nebo zadejte ID řetězce. Po dokončení stiskněte enter.

   Tento příklad používá **IDS_SAMPLE_ADDPAGE** pro název typu nové stránky vlastností.

1. Opakujte kroky 3 a 4 pomocí **IDS_SAMPLE_ADDPPG_CAPTION** pro ID a "Další stránka vlastností" pro titulek.

1. V . Soubor CPP nové třídy vlastností (v tomto `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` příkladu ) upravte tak, `CAddtlPropPage`aby IDS_SAMPLE_ADDPAGE je [předána třídou AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), jako v následujícím příkladu:

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Upravte konstruktor `CAddtlPropPage` tak, aby IDS_SAMPLE_ADDPPG_CAPTION `COlePropertyPage` je předán konstruktoru takto:

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Po provedené nezbytné změny znovu sestavit projekt a pomocí testovacího kontejneru otestovat novou stránku vlastností. Informace o tom, jak získat přístup k testovacímu kontejneru, najdete v tématu [Testování vlastností a událostí s testovacím kontejnerem.](../mfc/testing-properties-and-events-with-test-container.md)

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
