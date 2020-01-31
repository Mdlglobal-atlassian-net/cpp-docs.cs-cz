---
title: 'Návod: Vytvoření jednoduché aplikace pásu karet pomocí knihovny MFC'
ms.date: 09/09/2019
helpviewer_keywords:
- ribbon application, creating (MFC)
- creating a ribbon application (MFC)
ms.assetid: e61393e2-1d6b-4594-a7ce-157d3d1b0d9f
ms.openlocfilehash: 0f81b27d479b15864302b21a467bff9489ba465a
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821919"
---
# <a name="walkthrough-creating-a-ribbon-application-by-using-mfc"></a>Návod: Vytvoření jednoduché aplikace pásu karet pomocí knihovny MFC

Tento návod ukazuje, jak pomocí **Průvodce aplikací knihovny MFC** vytvořit aplikaci, která má ve výchozím nastavení pás karet. Pás karet pak můžete rozbalit přidáním **vlastní** kategorie pásu karet, která má panel pásu karet **Oblíbené** a následně na panel Přidat některé často používané příkazy.

## <a name="prerequisites"></a>Požadavky

Tento návod předpokládá, že jste nastavili sadu Visual Studio tak, aby používala **Obecné vývojové nastavení**. Používáte-li různá nastavení, nemusí být zobrazeny některé prvky uživatelského rozhraní, které jsou odkazovány v následujících pokynech.

### <a name="to-create-an-mfc-application-that-has-a-ribbon"></a>Vytvoření aplikace MFC obsahující pás karet

1. Použijte **Průvodce aplikací knihovny MFC** k vytvoření aplikace MFC, která má pás karet. Pokyny k otevření Průvodce pro vaši verzi sady Visual Studio najdete v tématu [Návod: použití nových ovládacích prvků prostředí MFC](walkthrough-using-the-new-mfc-shell-controls.md) .

1. V **Průvodci aplikací knihovny MFC**nastavte následující možnosti:

    1. V části **Typ aplikace** v části **vizuální styl a barvy**vyberte možnost **Office 2007 (modrý motiv)** .

    1. V části **Podpora složených dokumentů** se ujistěte, že není vybraná **možnost žádná** .

    1. V části **Vlastnosti šablony dokumentu** zadejte do pole **Přípona souboru** příponu názvu souboru pro dokumenty, které tato aplikace vytvoří, například *mfcrbnapp*.

    1. V části **Podpora databáze** (pouze Visual Studio 2015) Zkontrolujte, že není vybraná **možnost žádná** .

    1. V části **funkce uživatelského rozhraní** se ujistěte, že je vybraná **možnost použít pás karet** .

    1. Ve výchozím nastavení **Průvodce aplikací knihovny MFC** přidává podporu pro několik ukotvených podoken. Tyto možnosti lze z aplikace odstranit, protože tento návod pouze prezentuje pás karet. V části **Pokročilé funkce** zrušte zaškrtnutí všech možností.

1. Kliknutím na tlačítko **Dokončit** vytvořte aplikaci MFC.

1. Chcete-li ověřit, zda byla aplikace vytvořena správně, sestavte ji a spusťte. Chcete-li sestavit aplikaci, klikněte v nabídce **sestavení** na příkaz **Sestavit řešení**. Pokud se aplikace úspěšně sestaví, spusťte ji kliknutím na možnost **Spustit ladění** v nabídce **ladění** .

    Průvodce automaticky vytvoří pás karet, který má jednu kategorii pásu karet s názvem **Home**. Tento pás karet obsahuje tři panely pásu karet, které mají název **Schránka**, **zobrazení**a **okno**.

### <a name="to-add-a-category-and-panel-to-the-ribbon"></a>Přidání kategorie a panelu na pás karet

1. Chcete-li otevřít prostředek pásu karet, který průvodce vytvořil, přejděte v nabídce **zobrazení** na položku **ostatní okna** a klikněte na příkaz **prostředky**. V **prostředky**klikněte na **pás karet** a potom poklikejte na **IDR_RIBBON**.

1. Nejdřív přidejte vlastní kategorii na pás karet dvojitým kliknutím na **kategorie** v **sadě nástrojů**.

    Vytvoří se kategorie s titulkem **Category1** . Kategorie standardně obsahuje jeden panel.

    Klikněte pravým tlačítkem na **Category1** a pak klikněte na **vlastnosti**. V okně **vlastnosti** změňte **Titulek** na *vlastní*.

    Vlastnosti **velkých obrázků** a **malých obrázků** určují rastrové obrázky, které se používají jako ikony pro prvky pásu karet v této kategorii. Jelikož je tvorba vlastních rastrových obrázků nad rámec tohoto návodu, stačí použít obrázky vytvořené průvodcem. Malé rastrové obrázky mají velikost 16 × 16 pixelů. U malých imagí použijte rastrové obrázky, ke kterým se přistupuje `IDB_FILESMALL`m ID prostředku. Velké rastrové obrázky mají velikost 32 × 32 pixelů. U rozsáhlých imagí použijte rastrové obrázky, ke kterým se přistupuje `IDB_FILELARGE`m ID prostředku.

    > [!NOTE]
    > Na displejích s vysokým počtem bodů na palec (HDPI) jsou automaticky použity HDPI verze obrázků.

1. Dále panel přizpůsobte. Panely se používají k seskupování položek, které spolu logicky souvisejí. Například na kartě **Domů** této aplikace jsou příkazy **Vyjmout**, **Kopírovat**a **Vložit** umístěny na panelu **schránky** . Pokud chcete panel přizpůsobit, klikněte pravým tlačítkem na **ovládacího Panel1 (** a pak klikněte na **vlastnosti**. V okně **vlastnosti** změňte **Titulek** na *Oblíbené*.

    Můžete určit **index obrázku** pro panel. Toto číslo určuje ikonu, která se zobrazí, pokud je panel pásu karet přidán na **panel nástrojů Rychlý přístup**. Ikona se nezobrazuje na panelu pásu karet samotného.

1. Chcete-li ověřit, zda byly kategorie a panel pásu karet správně vytvořeny, zobrazte náhled ovládacího prvku pásu karet. Na **panelu nástrojů editoru pásu karet**klikněte na tlačítko **testovat pás karet** . Na pásu karet by se měla zobrazit **vlastní** karta a panel **oblíbených položek** .

### <a name="to-add-elements-to-the-ribbon-panels"></a>Přidání prvků na panely pásu karet

1. Chcete-li přidat prvky do panelu, který jste vytvořili v předchozím postupu, přetáhněte ovládací prvky z části **Editor pásu karet** v **sadě nástrojů** na panel v zobrazení Návrh.

1. Nejprve přidejte tlačítko **Tisk** . Tlačítko **Tisk** bude obsahovat podnabídku, která obsahuje příkaz pro **Rychlý tisk** , který se tiskne pomocí výchozí tiskárny. Oba tyto příkazy jsou již pro tuto aplikaci definovány. Jsou umístěny v nabídce aplikace.

    Chcete-li vytvořit tlačítko **Tisk** , přetáhněte na panel nástroj tlačítko.

    V okně **vlastnosti** změňte vlastnost **ID** na **ID_FILE_PRINT**, která by již měla být definována. Změňte **Titulek** k *tisku*. Změňte **index obrázku** na *4*.

    Chcete-li vytvořit tlačítko **Rychlý tisk** , klikněte na sloupec hodnoty vlastnosti vedle **položky nabídky**a potom klikněte na tlačítko se třemi tečkami ( **...** ). V **editoru položek**klikněte na tlačítko neoznačené **Přidat** a vytvořte položku nabídky. V okně **vlastnosti** změňte **Titulek** na *rychlé tisk*, **ID** na *ID_FILE_PRINT_DIRECT*a **Obrázek** na *5*. Vlastnost image Určuje ikonu **rychlého tisku** v prostředku `IDB_FILESMALL` rastrového obrázku.

1. Chcete-li ověřit, zda byla tlačítka přidána na panel pásu karet, sestavte a spusťte aplikaci. Chcete-li sestavit aplikaci, klikněte v nabídce **sestavení** na příkaz **Sestavit řešení**. Pokud se aplikace úspěšně sestaví, spusťte aplikaci kliknutím na příkaz **Spustit ladění** v nabídce **ladění** . Mělo by se zobrazit tlačítko **Tisk** a pole se seznamem na panelu **Oblíbené** na **vlastní** kartě na pásu karet.

## <a name="next-steps"></a>Další kroky

[Postupy: Přizpůsobení panelu nástrojů Rychlý přístup](../mfc/how-to-customize-the-quick-access-toolbar.md)

[Postupy: Přizpůsobení tlačítka aplikace](../mfc/how-to-customize-the-application-button.md)

Komplexní ukázky naleznete v tématu [Samples (MFC Feature Pack)](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Viz také:

[Návody](../mfc/walkthroughs-mfc.md)<br/>
[Ukázky (balík funkcí MFC)](../overview/visual-cpp-samples.md)
