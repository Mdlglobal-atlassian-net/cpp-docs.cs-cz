---
title: 'Návod: Vytvoření jednoduché aplikace pásu karet pomocí knihovny MFC | Dokumentace Microsoftu'
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
ms.openlocfilehash: 21478cdfd96fc32efaa674d7ec4f838e2f6b989b
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026890"
---
# <a name="walkthrough-creating-a-ribbon-application-by-using-mfc"></a>Návod: Vytvoření jednoduché aplikace pásu karet pomocí knihovny MFC
Tento návod ukazuje, jak používat **Průvodce aplikací knihovny MFC** vytvořit aplikaci, která má ve výchozím nastavení pás karet. Na pásu karet můžete pak rozšířit tak, že přidáte **vlastní** kategorie pásu karet, který má **Oblíbené položky** pásu karet panelu a následně přidáním některých často používaných funkcí na panel.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento názorný průvodce předpokládá, že jste nastavili [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] používat **obecným vývojovým nastavením**. Používáte-li jiná nastavení, některé prvky uživatelského rozhraní (UI), na které se následující instrukce odkazují, nemusí být zobrazeny. Informace o tom, jak změnit nastavení, najdete v části [jak: Reset Your Settings](http://msdn.microsoft.com/c95c51be-e609-4769-abba-65e6beedec76).  
  
### <a name="to-create-an-mfc-application-that-has-a-ribbon"></a>Vytvoření aplikace MFC obsahující pás karet  
  
1.  Použití **Průvodce aplikací knihovny MFC** k vytvoření aplikace MFC obsahující pás karet. Spustit průvodce, na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** dialogového okna rozbalte **Visual C++** pod uzlem **nainstalované šablony**vyberte **MFC**a pak vyberte  **Aplikace MFC**. Zadejte název projektu, například *MFCRibbonApp*a potom klikněte na tlačítko **OK**.  
  
3.  První stránka **Průvodce aplikací knihovny MFC**, klikněte na tlačítko **Další**.  
  
4.  Na **typ aplikace** stránce v části **vizuální styl a barvy**vyberte **Office 2007 (modrý motiv)**. Ostatní nastavení ponechte beze změny. Klikněte na tlačítko **Další**.  
  
5.  Na **Podpora složených dokumentů** stránky, ujistěte se, že **žádný** je vybrána a potom klikněte na tlačítko **Další**.  
  
6.  Na **vlastnosti šablony dokumentu** stránku, **příponu souboru** zadejte příponu názvu souboru pro dokumenty, které tato aplikace vytváří, například *mfcrbnapp*. Klikněte na tlačítko **Další**.  
  
7.  Na **Podpora databáze** stránky, ujistěte se, že **žádný** je vybrána a potom klikněte na tlačítko **Další**.  
  
8.  Na **funkce uživatelského rozhraní** stránky, ujistěte se, že **použít pás karet** zaškrtnuto. Klikněte na tlačítko **Další**.  
  
9. Ve výchozím nastavení **Průvodce aplikací knihovny MFC** přidává podporu několika podoken s podporou ukotvení. Tyto možnosti lze z aplikace odstranit, protože tento návod pouze prezentuje pás karet. Na **rozšířené funkce** stránce, zrušte zaškrtnutí všech možností. Klikněte na tlačítko **Další**.  
  
10. Na **třídy generované v** klikněte na **Dokončit** k vytvoření aplikace knihovny MFC.  
  
11. Chcete-li ověřit, zda byla aplikace vytvořena správně, sestavte ji a spusťte. Jak vytvořit aplikaci, na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Je-li aplikace sestavena úspěšně, spusťte ji kliknutím **spustit ladění** na **ladění** nabídky.  
  
     Průvodce automaticky vytvoří pás karet obsahující jednu kategorii pásu karet, který je pojmenován **Domů**. Tento pás karet obsahuje tři panely pásu karet, které jsou pojmenovány **schránky**, **zobrazení**, a **okno**.  
  
### <a name="to-add-a-category-and-panel-to-the-ribbon"></a>Přidání kategorie a panelu na pás karet  
  
1.  Chcete-li otevřít prostředek pásu karet, který průvodce vytvořil na **zobrazení** nabídky, přejděte na **ostatní Windows** a potom klikněte na **zobrazení prostředků**. V **zobrazení prostředků**, klikněte na tlačítko **pásu karet** a potom dvakrát klikněte na panel **IDR_RIBBON**.  
  
2.  Nejprve dvojitým kliknutím přidejte na pás karet vlastní kategorii **kategorie** v **nástrojů**.  
  
     Kategorie s titulkem **Category1** se vytvoří. Kategorie standardně obsahuje jeden panel.  
  
     Klikněte pravým tlačítkem na **Category1** a potom klikněte na tlačítko **vlastnosti**. V **vlastnosti** okno Změnit **titulek** k *vlastní*.  
  
     **Large Images** a **Small Images** vlastnosti určují rastrové obrázky používané jako ikony pro prvky pásu karet v této kategorii. Jelikož je tvorba vlastních rastrových obrázků nad rámec tohoto návodu, stačí použít obrázky vytvořené průvodcem. Malé rastrové obrázky mají velikost 16 × 16 pixelů. Pro malé obrázky použijte rastrové obrázky, ke kterým se přistupuje pomocí ID prostředku IDB_FILESMALL. Velké rastrové obrázky mají velikost 32 × 32 pixelů. Pro velké obrázky použijte rastrové obrázky, ke kterým se přistupuje pomocí ID prostředku IDB_FILELARGE.  
  
    > [!NOTE]
    >  Na displejích s vysokým počtem bodů na palec (HDPI) jsou automaticky použity HDPI verze obrázků.  
  
3.  Dále panel přizpůsobte. Panely se používají k seskupování položek, které spolu logicky souvisejí. Třeba na **Domů** kartu této aplikace **Vyjmout**, **kopírování**, a **vložit** příkazy jsou umístěny na  **Schránka** panelu. Chcete-li panel přizpůsobit, klikněte pravým tlačítkem na **Panel1** a potom klikněte na tlačítko **vlastnosti**. V **vlastnosti** okno Změnit **titulek** k *Oblíbené*.  
  
     Můžete zadat **Index bitové kopie** pro panel. Toto číslo určuje ikonu, která se zobrazí, pokud je do panelu pásu karet **panelu nástrojů Rychlý přístup**. Ikona není zobrazena na panelu pásu karet samotném.  
  
4.  Chcete-li ověřit, zda byly kategorie a panel pásu karet správně vytvořeny, zobrazte náhled ovládacího prvku pásu karet. Na **nástrojů editoru pásu karet**, klikněte na tlačítko **testovat pás karet** tlačítko. A **vlastní** kartu a **Oblíbené** panelu má být zobrazena na pásu karet.  
  
### <a name="to-add-elements-to-the-ribbon-panels"></a>Přidání prvků na panely pásu karet  
  
1.  Chcete-li přidat prvky panel, který jste vytvořili v předchozím postupu, přetáhněte ovládací prvky z **Editor pásu karet** část **nástrojů** do panelu v zobrazení Návrh.  
  
2.  Nejprve přidejte **tisk** tlačítko. **Tisk** tlačítko bude mít podnabídku obsahující **rychlý tisk** příkaz, který dokument vytiskne na výchozí tiskárně. Oba tyto příkazy jsou již pro tuto aplikaci definovány. Jsou umístěny v nabídce aplikace.  
  
     Chcete-li vytvořit **tisk** tlačítko, přetáhněte na panel nástroj tlačítko.  
  
     V **vlastnosti** okno Změnit **ID** vlastnost **ID_FILE_PRINT**, která by již měla být definována. Změna **titulek** k *tisk*. Změna **Image Index** k *4*.  
  
     Chcete-li vytvořit **rychlý tisk** tlačítko, klikněte na sloupec hodnoty vlastnosti vedle **položky nabídky**a potom klikněte na tlačítko se třemi tečkami (**...** ). V **Editor položek**, kliknutím na nepopsané **přidat** tlačítko vytvoříte položku nabídky. V **vlastnosti** okno Změnit **titulek** k *rychlý tisk*, **ID** k *ID_FILE_PRINT_DIRECT*, a **Image** k *5*. Vlastnost Obrázek určuje ikonu Rychlý tisk v prostředku rastrového obrázku IDB_FILESMALL.  
  
3.  Chcete-li ověřit, zda byla tlačítka přidána na panel pásu karet, sestavte a spusťte aplikaci. Jak vytvořit aplikaci, na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Je-li aplikace sestavena úspěšně, spusťte aplikaci kliknutím **spustit ladění** na **ladění** nabídky. **Tisk** tlačítka a pole se seznamem pole na **Oblíbené** panelu na **vlastní** má zobrazit na pásu karet.  
  
## <a name="next-steps"></a>Další kroky  
 [Postupy: Přizpůsobení panelu nástrojů Rychlý přístup](../mfc/how-to-customize-the-quick-access-toolbar.md)  
  
 [Postupy: Přizpůsobení tlačítka aplikace](../mfc/how-to-customize-the-application-button.md)  
  
 Koncové ukázky, naleznete v tématu [ukázky (balík funkcí MFC)](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Návody](../mfc/walkthroughs-mfc.md)   
 [Ukázky (balík funkcí MFC)](../visual-cpp-samples.md)

