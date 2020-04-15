---
title: Podpora databáze, Průvodce aplikací knihovny MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.database
helpviewer_keywords:
- MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
ms.openlocfilehash: c13d56d2fee45e130aba81168188bec6d8828d51
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365883"
---
# <a name="database-support-mfc-application-wizard"></a>Podpora databáze, Průvodce aplikací knihovny MFC

Tato stránka obsahuje možnosti, které umožňují určit úroveň podpory databáze (v případě potřeby i zdroje dat) pro projekt.

- **Podpora databáze**

   Nastaví úroveň podpory databáze pro váš projekt.

   |Možnost|Popis|
   |------------|-----------------|
   |**Žádné**|Poskytuje žádnou podporu databáze. Toto je výchozí možnost.|
   |**Pouze soubory záhlaví**|Poskytuje základní úroveň podpory databáze pro vaši aplikaci. Pokud vyberete podporu ROZHRANÍ ODBC v části **Typ klienta**, Průvodce aplikací knihovny MFC zahrne do projektu soubor záhlaví AFXDB. H. Přidá knihovny odkazů, ale nevytvoří žádné třídy specifické pro databázi. Sady záznamů můžete vytvořit později a použít je ke kontrole a aktualizaci záznamů. Pokud vyberete podporu TECHNOLOGIE OLE DB v části **Typ klienta**, budou zahrnuty následující soubory hlaviček: ATLBASE. H AFXOLEDB. H ATLPLUS. H|
   |**Zobrazení databáze bez podpory souborů**|Obsahuje soubory hlaviček databáze, knihovny odkazů, zobrazení záznamů a sadu záznamů. (K dispozici pouze pro aplikace s možností **podpory architektury dokument/zobrazení** vybrané na stránce [Typ aplikace.)](../../mfc/reference/application-type-mfc-application-wizard.md) Tato možnost zahrnuje podporu dokumentů, ale žádnou podporu serializace. Pokud se rozhodnete zahrnout zobrazení databáze, je nutné zadat zdroj dat.|
   |**Zobrazení databáze s podporou souborů**|Obsahuje soubory hlaviček databáze, knihovny odkazů, zobrazení záznamů a sadu záznamů. (K dispozici pouze pro aplikace s možností **podpory architektury dokument/zobrazení** vybrané na stránce **Typ aplikace.)** Tato možnost podporuje serializaci dokumentů, kterou můžete použít například k aktualizaci souboru profilu uživatele. Databázové aplikace obvykle pracují na základě pro každý záznam, nikoli na základě pro každý soubor, a proto nepotřebují serializaci. Však může mít zvláštní použití pro serializaci. Pokud se rozhodnete zahrnout zobrazení databáze, je nutné zadat zdroj dat.|

   > [!NOTE]
   > Pokud v části **Podpora databáze**vyberete buď zobrazení databáze bez **podpory souborů,** nebo **zobrazení databáze s podporou souborů**, odvození třídy zobrazení se liší v závislosti na **výběru typu klienta** následujícím způsobem:

  - Pokud vyberete **rozhraní ODBC** v části **Typ klienta**, bude třída zobrazení aplikace odvozena od [příkazu CRecordView](../../mfc/reference/crecordview-class.md). Tato třída je přidružena k třídě [odvozené crecordset,](../../mfc/reference/crecordset-class.md)kterou pro vás také vytvoří Průvodce aplikací knihovny MFC. Tato možnost poskytuje formulářovou aplikaci, ve které se zobrazení záznamů používá k zobrazení a aktualizaci záznamů prostřednictvím sady záznamů.

  - Pokud vyberete **OLE DB** v části **Typ klienta**, pak je třída zobrazení odvozena od [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)a je přidružena k třídě [CTable](../../data/oledb/ctable-class.md) nebo [CCommand](../../data/oledb/ccommand-class.md)-derived.

- **Typ klienta**

   Označuje, zda projekt používá třídy OLE DB nebo ODBC.

   |Možnost|Popis|
   |------------|-----------------|
   |**OLE DB**|Je-li vybrána tato možnost, klepnutím na tlačítko **Zdroj dat** vyvoláte průvodce **vlastnostmi datového propojení,** který vám pomůže vytvořit připojení ke zdroji dat technologie OLE DB.|
   |**ODBC**|Když je tato možnost vybraná, klepnutím na tlačítko **Zdroj dat** vyvoláte průvodce **výběrem zdroje dat,** který vám pomůže vytvořit připojení ke zdroji dat ODBC.|

- **Zdroj dat**

   > [!NOTE]
   > Průvodce příjemcem KNIHOVNY OLE DB a Průvodce mfc ODBC není k dispozici v sadě Visual Studio 2019 a novějších. Stále můžete přidat funkce ručně. Další informace naleznete [v tématu Vytvoření příjemce bez použití průvodce](../../data/oledb/creating-a-consumer-without-using-a-wizard.md).

   Klepnutím na tlačítko **Zdroj dat** nastavte zdroj dat pomocí zadaného ovladače nebo zprostředkovatele a databáze. Pokud jste v možnosti **Typ klienta** vybrali technologie OLE DB, zobrazí se na tomto tlačítku dialogové okno **Vlastnosti datového spojení.** Pokud jste v možnosti **Typ klienta** vybrali rozhraní ODBC, toto tlačítko zobrazí dialogové okno **Vybrat zdroj dat.** Tato možnost je k dispozici pouze v případě, že se rozhodnete zahrnout zobrazení databáze v aplikaci.

   |Možnost|Popis|
   |------------|-----------------|
   |**Vlastnosti datového propojení** (OLE DB)|Vytvoří zadaný zdroj dat pomocí zadaného zprostředkovatele TECHNOLOGIE OLE DB. Je nutné zadat zprostředkovatele TECHNOLOGIE OLE DB, umístění dat, zdroj dat, přihlašovací ID a (volitelně) heslo. Podrobnosti v tomto dialogovém okně naleznete v **tématu Zdroj dat** v [Průvodci příjemcem knihovny ATL OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md).|
   |**Vybrat zdroj dat** (ODBC)|Vytvoří zadaný zdroj dat pomocí zadaného ovladače ODBC. Chcete-li vybrat tabulku pro zdroj dat, musíte vybrat název zdroje dat. Průvodce sváže všechny sloupce tabulky s členskými `CRecordset`proměnnými odvozené třídy. Podrobnosti v tomto dialogovém okně naleznete v **tématu Zdroj dat** v [Průvodci příjemcem knihovny MFC ODBC](../../mfc/reference/mfc-odbc-consumer-wizard.md).|

- **Generovat přidělenou databázovou třídu**

   K dispozici pouze pro klienta TECHNOLOGIE OLE DB. Určuje, zda jsou třídy databáze v generovaném projektu používány atributy.

- **Svázat všechny sloupce**

   K dispozici pouze pro klienta ODBC. Určuje, zda jsou všechny sloupce ve vybrané tabulce svázány. Pokud toto políčko vyberete, budou všechny sloupce svázány. Pokud toto políčko nevyberete, nebudou vázány žádné sloupce a je nutné je ručně svázat ve třídě sady záznamů.

- **Typ**

   K dispozici pouze pro klienta ODBC. Určuje, zda je sada záznamů dynaset nebo snímek, jak je popsáno v následující tabulce.

   |Možnost|Popis|
   |------------|-----------------|
   |**Dynamická sada**|Určuje, že sada záznamů je sada dynasetu. Dynasada je výsledkem dotazu, který poskytuje indexované zobrazení do dat dotazované databáze. Dynaset ukládá pouze integrální index původní data a tím nabízí zvýšení výkonu přes snímek. Index odkazuje přímo na každý záznam nalezený v důsledku dotazu a označuje, zda je záznam odebrán. Máte také přístup k aktualizovaným informacím v dotazovaných záznamech.|
   |**Snímek**|Určuje, že sada záznamů je snímek. Snímek je výsledkem dotazu a je zobrazení do databáze v jednom okamžiku. Všechny záznamy nalezené v důsledku dotazu jsou uloženy do mezipaměti, takže se nezobrazí žádné změny původních záznamů.|

## <a name="see-also"></a>Viz také

[MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)
