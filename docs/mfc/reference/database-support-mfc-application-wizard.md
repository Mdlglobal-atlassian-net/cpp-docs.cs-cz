---
title: Podpora databáze, Průvodce aplikací knihovny MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.database
helpviewer_keywords:
- MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
ms.openlocfilehash: a1e0519e1351a48bbd969168d62f163c9dde7e7e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323110"
---
# <a name="database-support-mfc-application-wizard"></a>Podpora databáze, Průvodce aplikací knihovny MFC

Tato stránka obsahuje možnosti, které vám umožňují určit úroveň databáze podporují (plus zdroji dat v případě potřeby) pro váš projekt.

- **Podpora databáze**

   Nastaví úroveň podpory databáze pro váš projekt.

   |Možnost|Popis|
   |------------|-----------------|
   |**Žádné**|Poskytuje podporu žádné databáze. Toto je výchozí možnost.|
   |**Jenom hlavičkové soubory**|Poskytuje základní úroveň podpory databáze pro vaši aplikaci. Pokud vyberete ODBC podporu v rámci **typ klienta**, Průvodce aplikací knihovny MFC zahrnuje v projektu soubor hlaviček AFXDB. H. Přidá knihoven, ale nevytvoří všechny třídy specifické pro databázi. Můžete vytvořit později sady záznamů a použít k prozkoumání a aktualizaci záznamů. Pokud vyberete OLE DB – podpora pod **typ klienta**, jsou zahrnuty následující soubory hlaviček: ATLBASE. H AFXOLEDB. H ATLPLUS. H|
   |**Zobrazení databází bez podpory souborů**|Obsahuje databázové soubory hlaviček, knihovnách, zobrazení záznamů a záznamů. (K dispozici pouze pro aplikace s **podpora architektury Document/view** možnosti vybrané v [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md) stránky.) Tato možnost zahrnuje podporu dokumentu, ale nepodporuje serializaci. Pokud budete chtít zahrnout zobrazení databáze, musíte zadat zdroj dat.|
   |**Zobrazení databází s podporou souborů**|Obsahuje databázové soubory hlaviček, knihovnách, zobrazení záznamů a záznamů. (K dispozici pouze pro aplikace s **podpora architektury Document/view** možnosti vybrané v **typ aplikace** stránky.) Tato volba podporuje serializaci dokumentu, který můžete použít, například k aktualizaci souboru profilu uživatele. Databázové aplikace je obvykle fungují na základě jednotlivé záznamy, nikoli na jednotlivé – soubor základ a proto není nutné serializace. Však mohou mít zvláštní použití pro serializaci. Pokud budete chtít zahrnout zobrazení databáze, musíte zadat zdroj dat.|

   > [!NOTE]
   > V části **databáze podporují**, pokud vyberete buď **databáze zobrazení bez podpory souborů** nebo **databáze zobrazení s podporou souborů**, odvození třídy zobrazení se liší v závislosti na vaše **typ klienta** výběr následujícím způsobem:

   - Pokud vyberete **ODBC** pod **typ klienta**, pak je odvozena z třídy zobrazení aplikace [CRecordView](../../mfc/reference/crecordview-class.md). Tato třída je přidružena [CRecordset](../../mfc/reference/crecordset-class.md)-odvozené třídy, které Průvodce aplikací MFC také vytvoří za vás. Tato možnost vám poskytne pomocí formuláře aplikace, ve kterém se zobrazením záznamu používá k zobrazit a aktualizovat záznamy prostřednictvím sady záznamů.

   - Pokud vyberete **OLE DB** pod **typ klienta**, pak zobrazení třídy je odvozen z [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), a je přidružený [CTable](../../data/oledb/ctable-class.md) nebo [CCommand](../../data/oledb/ccommand-class.md)-odvozené třídy.

- **Typ klienta**

   Označuje, zda váš projekt používá třídy OLE DB nebo ODBC.

   |Možnost|Popis|
   |------------|-----------------|
   |**OLE DB**|Pokud je vybraná tato možnost, kliknutím na tlačítko **zdroj dat** tlačítko vyvolá **vlastnosti propojení dat** Průvodce vám pomůže vytvořit připojení ke zdroji dat OLE DB.|
   |**ODBC**|Pokud je vybraná tato možnost, kliknutím na tlačítko **zdroj dat** tlačítko vyvolá **vybrat zdroj dat** Průvodce vám pomůže vytvořit připojení ke zdroji dat rozhraní ODBC.|

- **Zdroj dat**

   Klikněte na tlačítko **zdroj dat** tlačítko a nastavte zdroj dat s využitím konkrétní ovladač, zprostředkovatele nebo databáze. Pokud jste vybrali OLE DB v **typ klienta** toto tlačítko zobrazuje možnost, **vlastnosti propojení dat** dialogové okno. Pokud jste vybrali v ODBC **typ klienta** možnost, poskytuje toto tlačítko **vybrat zdroj dat** dialogové okno. Tato možnost je dostupná jenom v případě, že budete chtít zahrnout zobrazení databází ve vaší aplikaci.

   |Možnost|Popis|
   |------------|-----------------|
   |**Vlastnosti propojení dat** (OLE DB)|Vytvoří zadaný zdroj dat pomocí zadaného zprostředkovatele OLE DB. Zprostředkovatel OLE DB, umístění dat, zdroji dat, přihlašovací ID a (volitelně) heslo, je nutné zadat. Podrobnosti v tomto dialogovém okně najdete v tématu **zdroj dat** v [průvodce příjemcem ATL OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md).|
   |**Vyberte zdroj dat** (ODBC)|Vytvoří zadaný zdroj dat pomocí zadané ovladače rozhraní ODBC. Název zdroje dat k výběru tabulky pro zdroj dat, musíte vybrat. Průvodce vytvoří vazbu všechny sloupce v tabulce k členské proměnné `CRecordset`-odvozené třídy. Podrobnosti v tomto dialogovém okně najdete v tématu **zdroj dat** v [průvodce příjemcem MFC ODBC](../../mfc/reference/mfc-odbc-consumer-wizard.md).|

   > [!NOTE]
   > V předchozích verzích, kliknutím na posunu **zdroj dat** tlačítko Otevřít dialogové okno otevřít soubor a umožňuje tak vybrat soubor dat propojení (UDL). Tato funkce se už nepodporuje.

- **Vygenerovat třídu s atributy databáze**

   K dispozici technologie OLE DB pouze pro klienty. Určuje, zda databázové třídy v generovaném projektu používat atributy.

- **Vytvořit vazbu všech sloupců**

   K dispozici ODBC pouze pro klienty. Určuje, zda jsou všechny sloupce v tabulce vybrané vázány. Pokud zaškrtnete toto políčko, jsou všechny sloupce vázány; Pokud toto políčko nezaškrtnete, nejsou vázány žádné sloupce a je třeba svázat ručně ve třídě sady záznamů.

- **Typ**

   K dispozici ODBC pouze pro klienty. Určuje, zda je dynamická sada nebo snímku, záznamů, jak je popsáno v následující tabulce.

   |Možnost|Popis|
   |------------|-----------------|
   |**Dynamická sada**|Určuje, že je dynamická sada záznamů. Dynamická sada je výsledek dotazu, který poskytuje indexovaném pohledu na data dotazované databázi. Dynamická sada pouze celočíselný index tak, aby původní data ukládá do mezipaměti, a proto nabízí výkon získat snímek. Index odkazuje přímo na každý záznam najít jako výsledek dotazu a označuje, pokud záznam se odebere. Máte také přístup k aktualizované informace v záznamech poslal dotaz.|
   |**Snímek**|Určuje, že je sada záznamů snímku. Snímek je výsledek dotazu a je tak představu o databázi v jednom bodě v čase. Všechny záznamy nalezen jako výsledek dotazu jsou uložené v mezipaměti, takže se nezobrazí žádné změny původních záznamů.|

## <a name="see-also"></a>Viz také:

[MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)
