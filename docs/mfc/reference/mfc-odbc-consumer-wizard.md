---
title: Průvodce příjemcem knihovny MFC ODBC
ms.date: 05/09/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 20357646bbb7aa4fe00db43d8e77f9bf0b95c9b5
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525370"
---
# <a name="mfc-odbc-consumer-wizard"></a>Průvodce příjemcem knihovny MFC ODBC

::: moniker range="vs-2019"

Tento průvodce není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="vs-2017"

Tento průvodce nastavuje třídu sady záznamů rozhraní ODBC a datové vazby potřebné pro přístup k danému zdroji dat.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Zdroj dat**

  **Zdroj dat** tlačítko umožňuje nastavit zadaný zdroj dat pomocí zadané ovladače rozhraní ODBC. Další informace o souborech zdroje dat (DSN) najdete v tématu [zdroje dat souborů](/sql/odbc/reference/file-data-sources) v sadě SDK rozhraní ODBC.

  **Vybrat zdroj dat** dialogové okno obsahuje dvě karty:

  - **Soubor zdroje dat** kartu:

     **Hledat v** pole určuje adresář, do kterého chcete vybrat soubory se použije jako zdroj dat. Výchozí hodnota je \Program Files\ODBC\Data zdroje. Existující soubor zdroje dat (DSN soubory) se zobrazí v seznamu hlavních. Můžete buď nastavení zdrojů dat před pomocí **DSN souboru** kartě [správce zdrojů dat ODBC](/sql/odbc/admin/odbc-data-source-administrator), nebo vytvořit nové pomocí tohoto dialogového.

     Chcete-li vytvořit nový soubor zdroje dat z tohoto dialogového okna, klikněte na tlačítko `New` k zadání názvu DSN; **vytvořit nový zdroj dat** zobrazí se dialogové okno. V **vytvořit nový zdroj dat** dialogové okno pole, vyberte příslušný ovladač a klikněte na tlačítko `Next`; klikněte na tlačítko **Procházet**a vyberte název souboru, který se použije jako zdroj dat (budete muset vybrat "Všechny soubory" zobrazení – název zdroje dat souborů, jako jsou například soubory XLS); Klikněte na tlačítko `Next`a potom klikněte na tlačítko **Dokončit**. (Pokud jste vybrali soubor bez názvu DSN, zobrazí se specifický ovladač dialogového okna, jako je například "Nastavení rozhraní ODBC Microsoft Excel,", který se převést soubor do zdroje dat DSN.)

     > [!NOTE]
     > Můžete také vytvořit nový zdroj dat souboru předem pomocí Správce zdrojů dat ODBC. Z **Start** nabídce vyberte možnost **nastavení**, **ovládací panely**, **nástroje pro správu**, **datové zdroje (ODBC)** a potom **správce zdrojů dat ODBC**.

     **Název DSN** pole můžete zadat název pro zdroj dat souboru. Ujistěte se, že název DSN končí příslušnou příponu souboru, jako je například .xls pro Excelové soubory nebo .mdb pro přístup k souborům.

     Další informace o názvech zdrojů dat, naleznete v tématu [zdroje dat souborů](/sql/odbc/reference/file-data-sources) v sadě SDK rozhraní ODBC.

  - **Zdroj dat pro počítač** kartu:

     Tato karta obsahuje systém a zdroje dat uživatele. Zdroje dat uživatel jsou specifická pro uživatele na tomto počítači. Systémové zdroje dat je možné všichni uživatelé v tomto počítači nebo ve službě v celém systému. Zobrazit [zdroje dat Machine](/sql/odbc/reference/machine-data-sources) v sadě SDK rozhraní ODBC

     Další informace o zdroji dat rozhraní ODBC, naleznete v tématu [zdroje dat](/sql/odbc/reference/data-sources) v sadě SDK rozhraní ODBC.

  Kliknutím na **OK** vytváření dokončete. **Vyberte databázový objekt** zobrazí se dialogové okno. V tomto dialogovém okně vyberte tabulku nebo zobrazení, že uživatel použije. Mějte na paměti, podržte klávesu CTRL a kliknutím na položky můžete vybrat víc zobrazení a tabulky. Kliknutím na **OK** vytváření dokončete.

- **Třída**

      The name of the consumer class, based by default on the name of the file or machine data source that you selected.

- **.h file**

   Název souboru hlaviček třídy příjemce ve výchozím nastavení na základě názvu souboru nebo počítače zdroje dat, který jste vybrali.

- **soubor .cpp**

   Název souboru implementace třídy příjemce ve výchozím nastavení na základě názvu souboru nebo počítače zdroje dat, který jste vybrali.

- **Typ**

   Určuje, zda je záznamů dynamická sada (výchozí) nebo snímku.

   - **Dynaset**: Určuje, že je dynamická sada záznamů. Dynamická sada je výsledek dotazu, který poskytuje indexovaném pohledu na data dotazované databázi. Dynamická sada pouze celočíselný index tak, aby původní data ukládá do mezipaměti, a proto nabízí výkon získat snímek. Index odkazuje přímo na každý záznam najít jako výsledek dotazu a označuje, pokud záznam se odebere. Máte také přístup k aktualizované informace v záznamech poslal dotaz. Toto nastavení je výchozí.

   - **Snímek**: Určuje, že je sada záznamů snímku. Snímek je výsledek dotazu a je tak představu o databázi v jednom bodě v čase. Všechny záznamy nalezen jako výsledek dotazu jsou uložené v mezipaměti, takže se nezobrazí žádné změny původních záznamů.

- **Vytvořit vazbu všech sloupců**

   Určuje, zda jsou všechny sloupce v tabulce vybrané vázány. Pokud vyberete toto pole (výchozí), jsou všechny sloupce vázány; Pokud toto políčko nezaškrtnete, nejsou vázány žádné sloupce a je třeba svázat ručně ve třídě sady záznamů.

::: moniker-end

## <a name="see-also"></a>Viz také:

[Knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)
