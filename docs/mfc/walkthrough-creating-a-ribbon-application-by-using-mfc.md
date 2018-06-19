---
title: 'Návod: Vytvoření jednoduché aplikace pásu karet pomocí knihovny MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon application, creating (MFC)
- creating a ribbon aplication (MFC)
ms.assetid: e61393e2-1d6b-4594-a7ce-157d3d1b0d9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f715830c110f03811202d2e98dc097bfe712208
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385226"
---
# <a name="walkthrough-creating-a-ribbon-application-by-using-mfc"></a>Návod: Vytvoření jednoduché aplikace pásu karet pomocí knihovny MFC
Tento návod ukazuje, jak používat **Průvodce aplikací knihovny MFC** vytvořit aplikaci, která má ve výchozím nastavení pásu karet. Na pásu karet můžete rozbalit přidáním **vlastní** kategorie pásu karet, který má **oblíbených položek** pásu karet panelech a pak přidáte některé často používané příkazy do panelu.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento návod předpokládá, že jste si nastavili [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] používat **obecné nastavení vývoj**. Používáte-li jiná nastavení, některé prvky uživatelského rozhraní (UI), na které se následující instrukce odkazují, nemusí být zobrazeny. Informace o tom, jak změnit nastavení najdete v tématu [postupy: obnovení vaše nastavení](http://msdn.microsoft.com/en-us/c95c51be-e609-4769-abba-65e6beedec76).  
  
### <a name="to-create-an-mfc-application-that-has-a-ribbon"></a>Vytvoření aplikace MFC obsahující pás karet  
  
1.  Použití **Průvodce aplikací knihovny MFC** k vytvoření aplikace knihovny MFC, který má pásu karet. Spuštění průvodce, na **soubor** nabídce přejděte na **nový**a potom klikněte na **projektu**.  
  
2.  V **nový projekt** dialogové okno, rozbalte seznam **Visual C++** pod uzlem **nainstalovaných šablonách**, vyberte **MFC**a potom vyberte  **Aplikace MFC**. Zadejte název projektu, například `MFCRibbonApp`a potom klikněte na **OK**.  
  
3.  Na první stránce **Průvodce aplikací knihovny MFC**, klikněte na tlačítko **Další**.  
  
4.  Na **typ aplikace** v části **vizuálního stylu a barvy**, vyberte **Office 2007 (motiv modrý)**. Ostatní nastavení ponechte beze změny. Klikněte na tlačítko **Další**.  
  
5.  Na **složené podporu dokumentu** stránky, ujistěte se, že **žádné** je vybrána a potom klikněte na **Další**.  
  
6.  Na **vlastnosti šablony dokumentu** stránky v **příponu souboru** zadejte příponu názvu souboru pro dokumenty, které vytvoří tuto aplikaci, například `mfcrbnapp`. Klikněte na tlačítko **Další**.  
  
7.  Na **podpory databáze** stránky, ujistěte se, že **žádné** je vybrána a potom klikněte na **Další**.  
  
8.  Na **funkce uživatelského rozhraní** stránky, ujistěte se, že **použít pásu karet** je vybrána. Klikněte na tlačítko **Další**.  
  
9. Ve výchozím nastavení **Průvodce aplikací knihovny MFC** přidává podporu pro několik ukotvení podokna. Tyto možnosti lze z aplikace odstranit, protože tento návod pouze prezentuje pás karet. Na **upřesňující funkce** zrušte zaškrtnutí všech možností. Klikněte na tlačítko **Další**.  
  
10. Na **vygenerované třídy** klikněte na tlačítko **Dokončit** k vytvoření aplikace MFC.  
  
11. Chcete-li ověřit, zda byla aplikace vytvořena správně, sestavte ji a spusťte. Vytvořit aplikaci, na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Pokud aplikace sestavení úspěšně, spusťte ji kliknutím **spustit ladění** na **ladění** nabídky.  
  
     Průvodce automaticky vytvoří pásu karet, který má jednu kategorii pásu karet, který je pojmenován **Domů**. Tato pásu karet obsahuje tři panely pásu karet, které jsou s názvem **schránky**, **zobrazení**, a **okno**.  
  
### <a name="to-add-a-category-and-panel-to-the-ribbon"></a>Přidání kategorie a panelu na pás karet  
  
1.  Otevřete prostředek pásu karet, které průvodce vytvořit, na **zobrazení** nabídky, přejděte na příkaz **ostatní okna** a pak klikněte na **zobrazení prostředků**. V **zobrazení prostředků**, klikněte na tlačítko **pásu karet** a potom dvakrát klikněte na **IDR_RIBBON**.  
  
2.  Nejprve přidat vlastní kategorii na pásu karet poklepáním **kategorie** v **sada nástrojů**.  
  
     Kategorie, která má popisek **kategorie 1** je vytvořena. Kategorie standardně obsahuje jeden panel.  
  
     Klikněte pravým tlačítkem na **kategorie 1** a pak klikněte na **vlastnosti**. V **vlastnosti** změňte **popisek** k `Custom`.  
  
     **Velkých obrázků** a **malých obrázků** vlastnosti zadejte rastrové obrázky, které jsou použity jako ikony pro prvky pásu karet v této kategorii. Jelikož je tvorba vlastních rastrových obrázků nad rámec tohoto návodu, stačí použít obrázky vytvořené průvodcem. Malé rastrové obrázky mají velikost 16 × 16 pixelů. Pro malé obrázky použijte rastrové obrázky, ke kterým se přistupuje pomocí ID prostředku IDB_FILESMALL. Velké rastrové obrázky mají velikost 32 × 32 pixelů. Pro velké obrázky použijte rastrové obrázky, ke kterým se přistupuje pomocí ID prostředku IDB_FILELARGE.  
  
    > [!NOTE]
    >  Na displejích s vysokým počtem bodů na palec (HDPI) jsou automaticky použity HDPI verze obrázků.  
  
3.  Dále panel přizpůsobte. Panely se používají k seskupování položek, které spolu logicky souvisejí. Například **Domů** kartě této aplikace **Vyjmout**, **kopie**, a **vložení** příkazy jsou umístěny na  **Schránky** panelu. Chcete-li přizpůsobit panel, klikněte pravým tlačítkem na **Panel1** a pak klikněte na **vlastnosti**. V **vlastnosti** změňte **popisek** k `Favorites`.  
  
     Můžete zadat **Index bitové kopie** pro panel. Tato hodnota určuje ikona, která se zobrazí v případě panelu pásu karet je přidán do **nástrojů Rychlý přístup**. Ikona není zobrazena na panelu pásu karet samotném.  
  
4.  Chcete-li ověřit, zda byly kategorie a panel pásu karet správně vytvořeny, zobrazte náhled ovládacího prvku pásu karet. Na **panelu nástrojů editoru pásu karet**, klikněte na tlačítko **pásu karet testovací** tlačítko. A **vlastní** kartě a **Oblíbené** panelu se má zobrazit na pásu karet.  
  
### <a name="to-add-elements-to-the-ribbon-panels"></a>Přidání prvků na panely pásu karet  
  
1.  Můžete přidat prvky na panelu, který jste vytvořili v předchozím postupu, přetáhněte ovládací prvky z **pásu karet Editor** části **sada nástrojů** do panelu v zobrazení návrhu.  
  
2.  Nejprve přidejte **tiskových** tlačítko. **Tiskových** tlačítko bude mít dílčí, který obsahuje **rychlý tisk** příkaz, který vytiskne pomocí výchozí tiskárny. Oba tyto příkazy jsou již pro tuto aplikaci definovány. Jsou umístěny v nabídce aplikace.  
  
     Chcete-li vytvořit **tiskových** tlačítko, přetáhněte nástroj tlačítka na panelu.  
  
     V **vlastnosti** změňte **ID** vlastnost **id_file_print –**, který by měl již být definován. Změna **popisek** k `Print`. Změna **obrázek indexu** k `4`.  
  
     Chcete-li vytvořit **rychlý tisk** tlačítko, klikněte ve sloupci Hodnota vlastnosti vedle **položky nabídky**a pak klikněte na tlačítko se třemi tečkami (**...** ). V **položky Editor**, klikněte na bez popisku **přidat** tlačítko vytvořte položku nabídky. V **vlastnosti** změňte **popisek** k `Quick Print`, **ID** k `ID_FILE_PRINT_DIRECT`, a **Image** k `5` . Vlastnost Obrázek určuje ikonu Rychlý tisk v prostředku rastrového obrázku IDB_FILESMALL.  
  
3.  Chcete-li ověřit, zda byla tlačítka přidána na panel pásu karet, sestavte a spusťte aplikaci. Vytvořit aplikaci, na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Pokud aplikace sestavení úspěšně, spusťte aplikaci kliknutím **spustit ladění** na **ladění** nabídky. **Tiskových** tlačítko a se seznamem se pole na **Oblíbené** panelu na **vlastní** se má zobrazit na pásu karet.  
  
## <a name="next-steps"></a>Další kroky  
 [Postupy: Přizpůsobení panelu nástrojů Rychlý přístup](../mfc/how-to-customize-the-quick-access-toolbar.md)  
  
 [Postupy: Přizpůsobení tlačítka aplikace](../mfc/how-to-customize-the-application-button.md)  
  
 Ukázky začátku do konce naleznete v části [ukázky (MFC Feature Pack)](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Návody](../mfc/walkthroughs-mfc.md)   
 [Ukázky (MFC Feature Pack)](../visual-cpp-samples.md)

