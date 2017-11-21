---
title: "Ovládací prvky MFC ActiveX: Přidání další stránky přizpůsobených vlastností | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 225535055f05fa8d6eeb08476004fbc5074e86b2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC – ovládací prvky ActiveX: Přidání další stránky přizpůsobených vlastností
Ovládací prvek ActiveX v některých případech bude mít více vlastností než to bude přiměřeně vejde na jednu stránku vlastností. V takovém případě můžete přidat stránky vlastností do ovládacího prvku ActiveX k zobrazení těchto vlastností.  
  
 Tento článek popisuje přidání nové stránky vlastností pro ovládací prvek ActiveX, který již má alespoň jednu stránku vlastností. Další informace o přidání uložených vlastností stránky (písma, obrázek nebo barvu), najdete v článku [MFC – ovládací prvky ActiveX: použití stránek vlastností Stock](../mfc/mfc-activex-controls-using-stock-property-pages.md).  
  
 Následující postupy použijte rozhraní ovládacího prvku ActiveX ukázka vytvořené Průvodce ovládacím prvkem ActiveX. Názvy tříd a identifikátory proto jsou jedinečné pro tento příklad.  
  
 Další informace o použití stránek vlastností v ovládacím prvku ActiveX najdete v následujících článcích:  
  
-   [Ovládací prvky MFC ActiveX: Stránky vlastností](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [Ovládací prvky MFC ActiveX: Použití stránek uložených vlastností](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
    > [!NOTE]
    >  Důrazně doporučujeme tuto novou vlastnost, kterou stránky dodržovat velikost standard pro stránky vlastností ovládacího prvku ActiveX. Stránky uložených vlastností obrázků a barvu měr 250 × 62 jednotky dialogu (DLU). Stránka vlastností standardní písma je 250 x 110 dlu. Výchozí stránka vlastností vytvořené Průvodce ovládacím prvkem ActiveX používá standardní DLU 250 × 62.  
  
### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Chcete-li vložit novou šablonu stránky vlastností do projektu  
  
1.  Pomocí řízení projektu otevřít otevřete zobrazení prostředků v pracovním prostoru projektu.  
  
2.  Klikněte pravým tlačítkem myši v zobrazení zdrojů otevřete místní nabídky a klikněte na tlačítko **přidat prostředek**.  
  
3.  Rozbalte **dialogové okno** uzel a vyberte možnost **IDD_OLE_PROPPAGE_SMALL**.  
  
4.  Klikněte na tlačítko `New` pro daný prostředek přidejte do projektu.  
  
5.  Vyberte novou šablonu, vlastnost stránku aktualizujte okno vlastností.  
  
6.  Zadejte novou hodnotu **ID** vlastnost. Tento příklad používá **IDD_PROPPAGE_NEWPAGE**.  
  
7.  Klikněte na tlačítko **Uložit** na panelu nástrojů.  
  
### <a name="to-associate-the-new-template-with-a-class"></a>Chcete-li přidružit nové šablony s třídou  
  
1.  Otevřete zobrazení tříd.  
  
2.  Klikněte pravým tlačítkem myši v zobrazení tříd a místní nabídce.  
  
3.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat třídu**.  
  
     Tím se otevře [přidat třídu](../ide/add-class-dialog-box.md) dialogové okno.  
  
4.  Dvakrát klikněte **třídy knihovny MFC** šablony.  
  
5.  V **název třídy** pole [Průvodce třídou MFC](../mfc/reference/mfc-add-class-wizard.md), zadejte název nové třídy dialogového okna. (V tomto příkladu `CAddtlPropPage`.)  
  
6.  Pokud chcete změnit názvy souborů, klikněte na tlačítko **změnit**. Zadáním názvů pro implementaci a hlavičky souborů, nebo přijměte výchozí názvy.  
  
7.  V **základní třída** vyberte `COlePropertyPage`.  
  
8.  V **dialogové okno ID** vyberte **IDD_PROPPAGE_NEWPAGE**.  
  
9. Klikněte na tlačítko **Dokončit** třídu vytvořte.  
  
 Povolit přístup k této nové stránky vlastností ovládacího prvku uživatele, proveďte následující změny do ovládacího prvku vlastnost stránky ID makro oddílu (nachází se v řídicím souboru implementace):  
  
 [!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]  
  
 Všimněte si, že musíte zvýšit druhý parametr `BEGIN_PROPPAGEIDS` makro (počet stránek vlastností) z 1 na 2.  
  
 Musíte také upravit řídicí soubor implementace (. Záhlaví souboru CPP) (. H) soubor nové třídy stránky vlastností.  
  
 Dalším krokem zahrnuje vytvoření dva nové prostředky řetězce, které vám poskytne název typu a popisek pro nové stránky vlastností.  
  
#### <a name="to-add-new-string-resources-to-a-property-page"></a>Přidání nových prostředků řetězec do stránky vlastností  
  
1.  Pomocí řízení projektu otevřít otevřete zobrazení prostředků.  
  
2.  Dvakrát klikněte **tabulky řetězců** složku a pak dvojitým kliknutím existující řetězec tabulky prostředků, do které chcete přidat řetězec.  
  
     Řetězec tabulka se otevře v okně.  
  
3.  Vyberte prázdný řádek na konec tabulky řetězec a zadejte text nebo popisek řetězce: například "Další stránka vlastností."  
  
     Tím se otevře **vlastnosti řetězce** stránky zobrazující **popisek** a **ID** polí. **Popisek** pole obsahuje řetězec, který jste zadali.  
  
4.  V **ID** pole, vyberte nebo zadejte ID pro řetězec. Po dokončení stiskněte klávesu Enter.  
  
     Tento příklad používá **IDS_SAMPLE_ADDPAGE** pro název typu nové stránky vlastností.  
  
5.  Zopakujte kroky 3 a 4 s využitím **IDS_SAMPLE_ADDPPG_CAPTION** pro ID a "Stránka další vlastnosti" titulek.  
  
6.  V. Soubor CPP nové třídy stránky vlastností (v tomto příkladu `CAddtlPropPage`) upravit `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` tak, aby je předaná IDS_SAMPLE_ADDPAGE [afxoleregisterpropertypageclass –](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), jako v následujícím příkladu:  
  
     [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]  
  
7.  Upravit konstruktoru `CAddtlPropPage` tak, aby **IDS_SAMPLE_ADDPPG_CAPTION** je předán `COlePropertyPage` konstruktoru, následujícím způsobem:  
  
     [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]  
  
 Po provedení nezbytné úpravy znovu sestavte projekt a otestovat kontejneru použít k testování nové stránky vlastností. V tématu [testování vlastností a událostí pomocí Test kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak přístup kontejner testů.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)

