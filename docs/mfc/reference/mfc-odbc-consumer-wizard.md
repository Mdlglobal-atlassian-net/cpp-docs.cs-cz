---
title: Průvodce příjemcem knihovny MFC ODBC
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: fd7e8df6692889914af2dd060ac42ed4ca3ebb8b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446397"
---
# <a name="mfc-odbc-consumer-wizard"></a>Průvodce příjemcem knihovny MFC ODBC

::: moniker range="vs-2019"

Tento průvodce není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="<=vs-2017"

Tento průvodce nastaví třídu sady záznamů rozhraní ODBC a datové vazby potřebné pro přístup k zadanému zdroji dat.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Zdroj dat**

  Tlačítko **zdroj dat** umožňuje nastavit zadaný zdroj dat pomocí zadaného ovladače ODBC. Další informace o souborech zdrojů dat (DSN) najdete v tématu [Souborové zdroje dat](/sql/odbc/reference/file-data-sources) v sadě ODBC SDK.

  V dialogovém okně **Vybrat zdroj dat** jsou dvě karty:

  - Karta **zdroj dat souboru** :

     V poli **Hledat v** Určete adresář, ve kterém se mají vybrat soubory, které se mají použít jako zdroje dat. Výchozí hodnota je \Program Files\Common Files\ODBC\Data Sources. V hlavním seznamu se zobrazí existující Souborové zdroje dat (soubory. DSN). Můžete buď nastavit zdroje dat předem, pomocí karty **SOUBOROVÉ DSN** ve [Správci zdroje dat ODBC](/sql/odbc/admin/odbc-data-source-administrator)nebo vytvořit nové pomocí tohoto dialogového okna.

     Pokud chcete vytvořit nový soubor zdroje dat z tohoto dialogového okna, klikněte na `New` a zadejte název DSN. zobrazí se dialogové okno **vytvořit nový zdroj dat** . V dialogovém okně **vytvořit nový zdroj dat** vyberte příslušný ovladač a klikněte na `Next`; klikněte na **Procházet**a vyberte název souboru, který se má použít jako zdroj dat (Pokud chcete zobrazit soubory, které nejsou DSN, třeba soubory. xls), vyberte všechny soubory. klikněte na `Next`a pak klikněte na **Dokončit**. (Pokud jste vybrali jiný soubor než DSN, zobrazí se dialogové okno specifické pro ovladač, jako je například nastavení ODBC Microsoft Excelu, které převede soubor na DSN.)

     > [!NOTE]
     > Nový souborový zdroj dat můžete také vytvořit předem pomocí Správce zdrojů dat ODBC. V nabídce **Start** vyberte **Nastavení**, **Ovládací panely**, **Nástroje pro správu**, **zdroje dat (ODBC)** a potom **Správce zdrojů dat ODBC**.

     Pole **název DSN** umožňuje zadat název zdroje dat souboru. Je nutné zajistit, aby název DSN byl ukončen odpovídající příponou souboru, například. xls pro soubory aplikace Excel nebo. mdb pro soubory Access.

     Další informace o DSN najdete v tématu [Souborové zdroje dat](/sql/odbc/reference/file-data-sources) v sadě ODBC SDK.

  - Karta **zdroje dat počítače** :

     Tato karta obsahuje seznam systémových a uživatelských zdrojů dat. Uživatelské zdroje dat jsou specifické pro uživatele v tomto počítači. Systémové zdroje dat mohou být použity všemi uživateli v tomto počítači nebo na službě v systému. Zobrazení [zdrojů dat počítačů](/sql/odbc/reference/machine-data-sources) v sadě ODBC SDK

     Další informace o zdrojích dat ODBC najdete v tématu [zdroje dat](/sql/odbc/reference/data-sources) v sadě ODBC SDK.

  Kliknutím na **OK** vytváření dokončete. Zobrazí se dialogové okno **Vybrat objekt databáze** . V tomto dialogovém okně vyberte tabulku nebo zobrazení, které bude příjemce používat. Všimněte si, že při kliknutí na položky můžete vybrat více zobrazení a tabulek, a to tak, že podržíte řídicí klíč. Kliknutím na **OK** vytváření dokončete.

- **Deník**

   Název třídy příjemce, který je ve výchozím nastavení založen na názvu souboru nebo zdroje dat počítače, který jste vybrali.

- **soubor. h**

   Název souboru hlaviček třídy příjemce, na základě výchozího názvu souboru nebo zdroje dat počítače, který jste vybrali.

- **soubor. cpp**

   Název implementačního souboru třídy příjemce, který je ve výchozím nastavení založen na názvu souboru nebo zdroje dat počítače, který jste vybrali.

- **Typ**

   Určuje, zda je sada záznamů sadou (výchozí) nebo snímkem.

   - **Dynamická sada**: Určuje, zda je sada záznamů sadou. Dynamická sada je výsledkem dotazu, který poskytuje indexované zobrazení na data dotazované databáze. Dynamická sada ukládá do původních dat pouze celočíselný index, a proto nabízí zvýšení výkonu snímku. Index odkazuje přímo na každý záznam, který byl nalezen jako výsledek dotazu, a určuje, zda byl odstraněn záznam. Máte také přístup k aktualizovaným informacím v dotazovaném záznamu. Toto nastavení je výchozí.

   - **Snapshot**: Určuje, zda je sada záznamů snímkem. Snímek je výsledkem dotazu a jedná se o zobrazení databáze v jednom bodě v čase. Všechny záznamy nalezené jako výsledek dotazu jsou uloženy v mezipaměti, takže neuvidíte žádné změny původních záznamů.

- **Vazba všech sloupců**

   Určuje, zda jsou všechny sloupce ve vybrané tabulce svázané. Pokud zaškrtnete toto políčko (výchozí nastavení), budou se svázat všechny sloupce. Pokud toto políčko nevyberete, nejsou svázány žádné sloupce a je nutné je vytvořit ručně ve třídě sady záznamů.

::: moniker-end

## <a name="see-also"></a>Viz také

[Využití MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)
