---
title: Podpora databáze, Průvodce aplikací knihovny MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.database
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86c6cd679b69bf84504d6735ca39d572bd48ff07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="database-support-mfc-application-wizard"></a>Podpora databáze, Průvodce aplikací knihovny MFC
Tato stránka obsahuje možnosti, které vám umožní určit úroveň databáze podporu pro svůj projekt (plus zdroj dat, v případě potřeby).  
  
 **Podpora databáze**  
 Nastaví úroveň podpory databáze pro váš projekt.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**None**|Poskytuje podporu žádné databáze. Toto je výchozí možnost.|  
|**Pouze soubory hlaviček**|Poskytuje základní úroveň podpory databáze pro vaši aplikaci. Pokud vyberete podpora rozhraní ODBC pod **typ klienta**, Průvodce aplikací MFC zahrnuje ve vašem projektu soubor hlaviček AFXDB. H. Přidá knihovny DLL, ale nevytvoří žádné třídy specifické pro databázi. Můžete vytvořit sady záznamů později a použít ji ke zkoumání a aktualizaci záznamů. Pokud vyberete podporu technologie OLE DB v části **typ klienta**, jsou zahrnuty následující soubory hlaviček: ATLBASE. H AFXOLEDB. H ATLPLUS. H|  
|**Zobrazení databáze bez podpory souborů**|Zahrnuje databázové soubory hlaviček, knihovny DLL, zobrazení záznamů a sadě záznamů. (K dispozici pouze pro aplikace s **Document/view – architektura podporu** možnosti vybrané v [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md) stránky.) Tato možnost zahrnuje podporu dokumentu, ale nepodporuje serializaci. Pokud se rozhodnete zahrnout zobrazení databáze, musíte zadat zdroj dat.|  
|**Zobrazení databáze s podporou souboru**|Zahrnuje databázové soubory hlaviček, knihovny DLL, zobrazení záznamů a sadě záznamů. (K dispozici pouze pro aplikace s **Document/view – architektura podporu** možnosti vybrané v **typ aplikace** stránky.) Tato volba podporuje serializaci dokumentu, který můžete použít, například aktualizace souboru profilu uživatele. Databázové aplikace se obvykle fungují na základě na záznam, místo na po souborech a tak nemusí serializace. Ale může mít zvláštní použití pro serializaci. Pokud se rozhodnete zahrnout zobrazení databáze, musíte zadat zdroj dat.|  
  
> [!NOTE]
>  V části **databáze podporují**, pokud vyberete buď **databáze zobrazení bez podpory souboru** nebo **databáze zobrazení s podporou souboru**, odvození třídy zobrazení se liší, v závislosti na vaše **typ klienta** výběr, následujícím způsobem:  
  
-   Pokud vyberete **ODBC** pod **typ klienta**, pak je odvozena od třídy zobrazení aplikace [CRecordView](../../mfc/reference/crecordview-class.md). Tato třída je přidružen [CRecordset](../../mfc/reference/crecordset-class.md)-odvozené třídy, které pro vás také vytvoří Průvodce aplikací MFC. Tato možnost poskytuje k aplikaci založené na formulářích, ve kterém zobrazení záznamů slouží k zobrazení a aktualizaci záznamů prostřednictvím sady záznamů.  
  
-   Pokud vyberete **OLE DB** pod **typ klienta**, pak je odvozena od třídy zobrazení [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), a je přidružen [CTable](../../data/oledb/ctable-class.md) nebo [CCommand](../../data/oledb/ccommand-class.md)-odvozené třídy.  
  
 **Typ klienta**  
 Označuje, zda váš projekt používá třídy OLE DB nebo ODBC.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**OLE DB**|Pokud je vybraná tato možnost, kliknutím na tlačítko **zdroj dat** tlačítko vyvolá **vlastnosti propojení dat** Průvodce vám pomůže vytvořit připojení ke zdroji dat OLE DB.|  
|**ODBC**|Pokud je vybraná tato možnost, kliknutím na tlačítko **zdroj dat** tlačítko vyvolá **vybrat zdroj dat** Průvodce vám pomůže vytvořit připojení ke zdroji dat rozhraní ODBC.|  
  
 **Zdroj dat**  
 Klikněte **zdroj dat** tlačítko Nastavení zdroje dat pomocí zadaného ovladače nebo zprostředkovatele a databáze. Pokud jste vybrali OLE DB v **typ klienta** možnost, zobrazí toto tlačítko **vlastnosti propojení dat** dialogové okno. Pokud jste vybrali v ODBC **typ klienta** možnost, poskytuje toto tlačítko **vybrat zdroj dat** dialogové okno. Tato možnost je dostupná pouze v případě, že se rozhodnete zahrnout zobrazení databáze v aplikaci.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Vlastnosti propojení dat** (OLE DB)|Vytvoří zadaný zdroj dat pomocí zadaného zprostředkovatele OLE DB. Je nutné zadat zprostředkovatele OLE DB, umístění dat, zdroj dat, přihlašovací ID a (volitelně) heslo. Podrobnosti tohoto dialogového okna najdete v tématu **zdroj dat** v [průvodce příjemcem knihovny ATL technologie OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md).|  
|**Vyberte zdroj dat** (ODBC)|Vytvoří zadaný zdroj dat pomocí zadaný ovladač ODBC. Název zdroje dat vybrat tabulku pro zdroj dat, je nutné vybrat. Průvodce váže všechny sloupce tabulky k členské proměnné `CRecordset`-odvozené třídy. Podrobnosti tohoto dialogového okna najdete v tématu **zdroj dat** v [průvodce příjemcem knihovny MFC ODBC](../../mfc/reference/mfc-odbc-consumer-wizard.md).|  
  
> [!NOTE]
>  V předchozích verzích Shift a kliknutí na **zdroj dat** tlačítko Otevřít soubor otevřete dialogové okno a umožní vám vybrat soubor dat propojení (UDL). Tato funkce již není podporována.  
  
 **Generování databázové třídy atributů**  
 K dispozici pro jenom klient OLE DB. Určuje, zda použít databázové třídy v generovaném projektu atributy.  
  
 **Vytvoření vazby všechny sloupce**  
 K dispozici pro jenom klient ODBC. Určuje, zda jsou vázány všechny sloupce ve vybrané tabulce. Pokud zaškrtnete toto políčko, jsou všechny sloupce vázány; Pokud toto políčko nezaškrtnete, žádné sloupce je vázána a je třeba svázat ručně ve třídě sady záznamů.  
  
 **Typ**  
 K dispozici pro jenom klient ODBC. Určuje, zda je záznamů dynamická sada nebo snímek, jak je popsáno v následující tabulce.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Dynamická sada**|Určuje, že je dynamická sada záznamů. Dynamická sada je výsledkem dotazu, který poskytuje indexované zobrazení na data dotazované databázi. Dynamická sada pouze celočíselný index pro původní data ukládá do mezipaměti, a proto nabízí a výkonu získat přes snímek. Index odkazuje přímo na všech vybraných záznamech výsledkem dotazu a určuje, pokud je odebrat záznam. Máte také přístup k aktualizované informace v záznamech předmětem dotazu.|  
|Snímek|Určuje, že je záznamů snímku. Snímek je výsledek dotazu a zobrazení do databáze v jednom bodě v čase. Všechny záznamy nalezené v důsledku dotaz jsou v mezipaměti, takže se nezobrazí žádné změny původní záznamy.|  
  
## <a name="see-also"></a>Viz také  
 [MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)
