---
title: Průvodce příjemcem knihovny MFC ODBC
ms.date: 10/03/2018
f1_keywords:
- vc.codewiz.class.mfc.consumer.overview
helpviewer_keywords:
- MFC ODBC Consumer Wizard
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: f86eded7cc7c04a85b1bcd93e917bd5a2b5c9696
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590876"
---
# <a name="mfc-odbc-consumer-wizard"></a>Průvodce příjemcem knihovny MFC ODBC

> [!WARNING]
> V sadě Visual Studio 2017 verze 15.9 průvodce tento kód je zastaralá a v budoucí verzi systému Visual Studio se odebere. Tento průvodce je používána zřídka. Obecné podpory knihovny ATL a MFC nemá žádný vliv, odebráním tohoto průvodce. Pokud chcete sdílet svůj názor na toto vyřazení, vyplňte prosím [tento průzkum](https://www.surveymonkey.com/r/QDWKKCN). Vaše zpětná vazba záleží na nás.

Tento průvodce nastavuje třídu sady záznamů rozhraní ODBC a datové vazby potřebné pro přístup k danému zdroji dat.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Zdroj dat**

   **Zdroj dat** tlačítko umožňuje nastavit zadaný zdroj dat pomocí zadané ovladače rozhraní ODBC. Další informace o souborech zdroje dat (DSN) najdete v tématu [zdroje dat souborů](/previous-versions/windows/desktop/ms715401) v sadě SDK rozhraní ODBC.

   **Vybrat zdroj dat** dialogové okno obsahuje dvě karty:

   - **Soubor zdroje dat** kartu:

      **Hledat v** pole určuje adresář, do kterého chcete vybrat soubory se použije jako zdroj dat. Výchozí hodnota je \Program Files\ODBC\Data zdroje. Existující soubor zdroje dat (DSN soubory) se zobrazí v seznamu hlavních. Můžete buď nastavení zdrojů dat před pomocí **DSN souboru** kartě [správce zdrojů dat ODBC](/previous-versions/windows/desktop/ms714024), nebo vytvořit nové pomocí tohoto dialogového.

      Chcete-li vytvořit nový soubor zdroje dat z tohoto dialogového okna, klikněte na tlačítko `New` k zadání názvu DSN; **vytvořit nový zdroj dat** zobrazí se dialogové okno. V **vytvořit nový zdroj dat** dialogové okno pole, vyberte příslušný ovladač a klikněte na tlačítko `Next`; klikněte na tlačítko **Procházet**a vyberte název souboru, který se použije jako zdroj dat (budete muset vybrat "Všechny soubory" zobrazení – název zdroje dat souborů, jako jsou například soubory XLS); Klikněte na tlačítko `Next`a potom klikněte na tlačítko **Dokončit**. (Pokud jste vybrali soubor bez názvu DSN, zobrazí se specifický ovladač dialogového okna, jako je například "Nastavení rozhraní ODBC Microsoft Excel,", který se převést soubor do zdroje dat DSN.)

      > [!NOTE]
      > Můžete také vytvořit nový zdroj dat souboru předem pomocí Správce zdrojů dat ODBC. Z **Start** nabídce vyberte možnost **nastavení**, **ovládací panely**, **nástroje pro správu**, **datové zdroje (ODBC)** a potom **správce zdrojů dat ODBC**.

      **Název DSN** pole můžete zadat název pro zdroj dat souboru. Ujistěte se, že název DSN končí příslušnou příponu souboru, jako je například .xls pro Excelové soubory nebo .mdb pro přístup k souborům.

      Další informace o názvech zdrojů dat, naleznete v tématu [zdroje dat souborů](/previous-versions/windows/desktop/ms715401) v sadě SDK rozhraní ODBC.

   - **Zdroj dat pro počítač** kartu:

      Tato karta obsahuje systém a zdroje dat uživatele. Zdroje dat uživatel jsou specifická pro uživatele na tomto počítači. Systémové zdroje dat je možné všichni uživatelé v tomto počítači nebo ve službě v celém systému. Zobrazit [zdroje dat Machine](/previous-versions/windows/desktop/ms710952) v sadě SDK rozhraní ODBC

      Další informace o zdroji dat rozhraní ODBC, naleznete v tématu [zdroje dat](/previous-versions/windows/desktop/ms711688) v sadě SDK rozhraní ODBC.

   Klikněte na tlačítko **OK** na dokončení. **Vyberte databázový objekt** zobrazí se dialogové okno. V tomto dialogovém okně vyberte tabulku nebo zobrazení, že uživatel použije. Mějte na paměti, podržte klávesu CTRL a kliknutím na položky můžete vybrat víc zobrazení a tabulky. Klikněte na tlačítko **OK** na dokončení.

- **Třída**

      The name of the consumer class, based by default on the name of the file or machine data source that you selected.

- **soubor .h**

   Název souboru hlaviček třídy příjemce ve výchozím nastavení na základě názvu souboru nebo počítače zdroje dat, který jste vybrali.

- **soubor .cpp**

   Název souboru implementace třídy příjemce ve výchozím nastavení na základě názvu souboru nebo počítače zdroje dat, který jste vybrali.

- **Typ**

   Určuje, zda je záznamů dynamická sada (výchozí) nebo snímku.

   - **Dynamická sada**: Určuje, že je dynamická sada záznamů. Dynamická sada je výsledek dotazu, který poskytuje indexovaném pohledu na data dotazované databázi. Dynamická sada pouze celočíselný index tak, aby původní data ukládá do mezipaměti, a proto nabízí výkon získat snímek. Index odkazuje přímo na každý záznam najít jako výsledek dotazu a označuje, pokud záznam se odebere. Máte také přístup k aktualizované informace v záznamech poslal dotaz. Toto nastavení je výchozí.

   - **Snímek**: Určuje, že je sada záznamů snímku. Snímek je výsledek dotazu a je tak představu o databázi v jednom bodě v čase. Všechny záznamy nalezen jako výsledek dotazu jsou uložené v mezipaměti, takže se nezobrazí žádné změny původních záznamů.

- **Vytvořit vazbu všech sloupců**

   Určuje, zda jsou všechny sloupce v tabulce vybrané vázány. Pokud vyberete toto pole (výchozí), jsou všechny sloupce vázány; Pokud toto políčko nezaškrtnete, nejsou vázány žádné sloupce a je třeba svázat ručně ve třídě sady záznamů.

## <a name="see-also"></a>Viz také

[Knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)

