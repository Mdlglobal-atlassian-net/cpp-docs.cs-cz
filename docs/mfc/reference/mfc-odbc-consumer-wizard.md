---
title: Průvodce příjemcem knihovny MFC ODBC
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 45087434c0093f99383096761d58a8029c9d5009
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373023"
---
# <a name="mfc-odbc-consumer-wizard"></a>Průvodce příjemcem knihovny MFC ODBC

::: moniker range="vs-2019"

Tento průvodce není k dispozici v sadě Visual Studio 2019 a novějších.

::: moniker-end

::: moniker range="<=vs-2017"

Tento průvodce nastaví třídu sady záznamů ODBC a datové vazby potřebné pro přístup k zadanému zdroji dat.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Zdroj dat**

  Tlačítko **Zdroj dat** umožňuje nastavit zadaný zdroj dat pomocí zadaného ovladače ODBC. Další informace o souborech zdrojů dat (DSN) naleznete v [tématu Zdroje dat souborů](/sql/odbc/reference/file-data-sources) v sadě ODBC SDK.

  Dialogové okno **Vybrat zdroj dat** má dvě karty:

  - Karta **Zdroj dat souboru:**

     Pole **Hledat v** určuje adresář, ve kterém chcete vybrat soubory, které mají být použity jako zdroje dat. Výchozí hodnota je \Program Files\Common Files\ODBC\Data Sources. Existující zdroje dat souborů (soubory DSN) se zobrazí v hlavním seznamu. Zdroje dat můžete nastavit předem pomocí karty **DSN souboru** ve [správci zdroje dat ODBC](/sql/odbc/admin/odbc-data-source-administrator)nebo vytvořit nové pomocí tohoto dialogového okna.

     Chcete-li vytvořit nový zdroj dat souboru z tohoto dialogového okna, klepněte `New` na tlačítko pro určení názvu DSN. zobrazí se dialogové okno **Vytvořit nový zdroj dat.** V dialogovém okně **Vytvořit nový zdroj dat** `Next`vyberte příslušný ovladač a klepněte na ; klepněte na **tlačítko Procházet**a vyberte název souboru, který má být použit jako zdroj dat (chcete-li zobrazit soubory, které nejsou dsn, například soubory XLS, musíte vybrat možnost "Všechny soubory"); klepněte na tlačítko `Next`a potom klepněte na tlačítko **Dokončit**. (Pokud jste vybrali soubor, který není dsn, zobrazí se dialogové okno specifické pro ovladač, například "Instalace aplikace ODBC microsoft excel", které převede soubor na dsn.)

     > [!NOTE]
     > Nový zdroj dat souboru můžete také vytvořit předem pomocí správce zdroje dat ROZHRANÍ ODBC. V nabídce **Start** vyberte **Nastavení**, **Ovládací panely**, Nástroje pro **správu**, **Zdroje dat (ODBC)** a potom **správce zdroje dat ROZHRANÍ ODBC**.

     Pole **Název DSN** umožňuje zadat název zdroje dat souboru. Je třeba zajistit, aby název DSN skončil příslušnou příponou souboru, například .xls pro soubory aplikace Excel nebo .mdb pro soubory aplikace Access.

     Další informace o dsn svícen naleznete v [tématu Zdroje dat souborů](/sql/odbc/reference/file-data-sources) v sadě ODBC SDK.

  - Karta **Zdroj dat stroje:**

     Na této kartě jsou uvedeny systémové a uživatelské zdroje dat. Zdroje uživatelských dat jsou specifické pro uživatele v tomto počítači. Systémové zdroje dat mohou používat všichni uživatelé v tomto počítači nebo ve službě celého systému. Viz [Zdroje dat počítače](/sql/odbc/reference/machine-data-sources) v sadě SDK ODBC

     Další informace o zdrojích dat ROZHRANÍ ODBC naleznete v [tématu Zdroje dat](/sql/odbc/reference/data-sources) v sadě ODBC SDK.

  Kliknutím na **OK** vytváření dokončete. Zobrazí se dialogové okno **Vybrat databázový objekt.** V tomto dialogovém okně vyberte tabulku nebo zobrazení, které bude spotřebitel používat. Všimněte si, že můžete vybrat více zobrazení a tabulek podržením ovládacího tlačítka při kliknutí na položky. Kliknutím na **OK** vytváření dokončete.

- **Třída**

   Název třídy příjemce, který je ve výchozím nastavení založen na názvu vybraného souboru nebo zdroje dat počítače.

- **Soubor H**

   Název souboru hlavičky třídy příjemce, který je ve výchozím nastavení založen na názvu vybraného souboru nebo zdroje dat počítače.

- **Soubor CPP**

   Název souboru implementace třídy příjemce, který je ve výchozím nastavení založen na názvu vybraného souboru nebo zdroje dat počítače.

- **Typ**

   Určuje, zda je sada záznamů dynaset (výchozí) nebo snímek.

  - **Dynaset**: Určuje, že sada záznamů je dynaset. Dynasada je výsledkem dotazu, který poskytuje indexované zobrazení do dat dotazované databáze. Dynaset ukládá pouze integrální index původní data a tím nabízí zvýšení výkonu přes snímek. Index odkazuje přímo na každý záznam nalezený v důsledku dotazu a označuje, zda je záznam odebrán. Máte také přístup k aktualizovaným informacím v dotazovaných záznamech. Toto nastavení je výchozí.

  - **Snímek**: Určuje, že sada záznamů je snímek. Snímek je výsledkem dotazu a je zobrazení do databáze v jednom okamžiku. Všechny záznamy nalezené v důsledku dotazu jsou uloženy do mezipaměti, takže se nezobrazí žádné změny původních záznamů.

- **Svázat všechny sloupce**

   Určuje, zda jsou všechny sloupce ve vybrané tabulce svázány. Pokud vyberete toto pole (výchozí), budou všechny sloupce svázány; Pokud toto políčko nevyberete, nebudou vázány žádné sloupce a je nutné je ručně svázat ve třídě sady záznamů.

::: moniker-end

## <a name="see-also"></a>Viz také

[Spotřebovávat rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)
