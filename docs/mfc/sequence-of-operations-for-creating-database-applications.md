---
title: Posloupnost operací při vytváření databázových aplikací
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: c393269d6af108ee82786e9d59f81aad11428157
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372777"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>Posloupnost operací při vytváření databázových aplikací

V následující tabulce jsou uvedeny vaše role a role rozhraní při psaní databázových aplikací.

> [!NOTE]
> Prostředí Visual C++ a průvodci nepodporují DAO (i když jsou zahrnuty třídy DAO a můžete je stále používat). Společnost Microsoft doporučuje použít rozhraní ODBC pro nové projekty knihovny MFC. DAO byste měli používat pouze při údržbě existujících aplikací.

### <a name="creating-database-applications"></a>Vytváření databázových aplikací

|Úkol|Vy děláte|Rámec neobsahuje|
|----------|------------|------------------------|
|Rozhodněte se, zda chcete použít třídy Knihovny MFC ODBC nebo DAO.|Použití rozhraní ODBC pro nové projekty knihovny MFC. DAO používejte pouze k údržbě existujících aplikací. Obecné informace naleznete v článku [Programování přístupu k datům](../data/data-access-programming-mfc-atl.md).|Rozhraní framework poskytuje třídy, které podporují přístup k databázi.|
|Vytvořte si kostru aplikace s možnostmi databáze.|Spusťte Průvodce aplikací knihovny MFC. Na stránce Podpora databáze vyberte možnosti. Pokud zvolíte možnost, která vytvoří zobrazení záznamu, určete také:<br /><br />- Zdroj dat a názvy tabulek nebo názvy<br />- Název nebo jména dotazu.|Průvodce aplikací knihovny MFC vytvoří soubory a určí potřebné zahrnuty. V závislosti na zadaných možnostech mohou soubory obsahovat třídu sady záznamů.|
|Navrhněte databázový formulář nebo formuláře.|Pomocí editoru dialogů Visual C++ umístěte ovládací prvky do prostředků šablony dialogu pro třídy zobrazení záznamů.|Průvodce aplikací knihovny MFC vytvoří prostředek šablony prázdného dialogu, který můžete vyplnit.|
|Podle potřeby vytvořte další třídy zobrazení záznamů a sady záznamů.|Pomocí zobrazení tříd vytvořte třídy a editor dialogů k návrhu zobrazení.|Zobrazení tříd vytvoří další soubory pro nové třídy.|
|Vytvořte objekty sady záznamů podle potřeby v kódu. Pomocí každé sady záznamů můžete manipulovat se záznamy...|Sady záznamů jsou založeny na třídách odvozených z [CRecordset](../mfc/reference/crecordset-class.md) s průvodci.|Rozhraní ODBC používá výměnu pole záznamů (RFX) k výměně dat mezi databází a datovými členy pole sady záznamů. Pokud používáte zobrazení záznamů, výměna dat dialogových oken (DDX) si vyměňuje data mezi sadou záznamů a ovládacími prvky v zobrazení záznamu.|
|... nebo vytvořte explicitní [CDatabase](../mfc/reference/cdatabase-class.md) v kódu pro každou databázi, kterou chcete otevřít.|Objekty sady záznamů založte na databázových objektech.|Databázový objekt poskytuje rozhraní ke zdroji dat.|
|Dynamicky spojte datové sloupce se sadou záznamů.|V rozhraní ODBC přidejte kód do odvozené třídy sady záznamů pro správu vazby. Viz článek [Recordset: Dynamicky vazebné datové sloupce (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||

## <a name="see-also"></a>Viz také

[Sestavení na základě rozhraní .NET Framework](../mfc/building-on-the-framework.md)<br/>
[Posloupnost operací při sestavování aplikací MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Posloupnost operací při vytváření aplikací OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[Posloupnost operací při vytváření ovládacích prvků ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)
