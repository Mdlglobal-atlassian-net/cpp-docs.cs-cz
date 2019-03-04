---
title: Posloupnost operací při vytváření databázových aplikací
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: efd6b12b186ce0ef1c0caf57f313f6aa50425fec
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283667"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>Posloupnost operací při vytváření databázových aplikací

Následující tabulka uvádí vaši roli a roli v rámci při psaní databázových aplikací.

> [!NOTE]
>  Prostředí Visual C++ a Průvodce nepodporuje rozhraní DAO (i když jsou součástí třídy DAO a můžete stále použít). Společnost Microsoft doporučuje použití rozhraní ODBC pro nové projekty MFC. DAO byste měli používat jenom v udržování existujících aplikací.

### <a name="creating-database-applications"></a>Vytváření databázových aplikací

|Úloha|Můžete provést|Nepodporuje rozhraní framework|
|----------|------------|------------------------|
|Rozhodněte, jestli se má použít třídy knihovny MFC rozhraní ODBC a DAO.|Použití rozhraní ODBC pro nové projekty MFC. Pouze k udržování existujících aplikací pomocí rozhraní DAO. Obecné informace najdete v článku [programování přístupu dat](../data/data-access-programming-mfc-atl.md).|Architektura dodává třídy, které podporují přístup k databázi.|
|Vytvoření kostru aplikace s možnostmi databáze.|Spuštění Průvodce aplikací knihovny MFC. Vyberte možnosti na stránce Podpora databáze. Pokud zvolíte možnost, která vytvoří zobrazení záznamů, také zadejte:<br /><br />– Data zdroje a název tabulky nebo názvy<br />-Dotazování název nebo názvy.|Průvodce aplikací MFC vytvoří soubory a určí, že obsahuje nezbytné. V závislosti na možnostech, které zadáte může obsahovat soubory třídy sady záznamů.|
|Návrh databáze formuláře nebo formuláře.|Pomocí dialogového okna editoru Visual C++ umístit ovládací prvky na prostředků šablony dialogového okna pro tříd zobrazení záznamu.|Průvodce aplikací MFC vytvoří prostředek šablony prázdné dialogového okna můžete vyplnit.|
|Podle potřeby vytvořte další záznam třídy zobrazení a sady záznamů.|Vytvoření třídy a dialogové okno k zobrazení návrhu editoru pomocí zobrazení tříd.|Zobrazení tříd vytvoří další soubory pro nové třídy.|
|Vytvořte sadu záznamů objekty podle potřeby ve vašem kódu. Každá sada záznamů slouží k manipulaci s záznamů...|Vaše sady záznamů jsou založeny na třídy odvozené od [CRecordset](../mfc/reference/crecordset-class.md) pomocí průvodců.|ODBC používá výměna pole záznamu (RFX) k výměně dat mezi databází a sady záznamů pole datových členů. Pokud používáte zobrazení záznamů, výměna dat dialogových oken (DDX) vyměňuje data mezi ovládacími prvky pro zobrazení záznamů a záznamů.|
|.. .nebo vytvořit explicitní [CDatabase](../mfc/reference/cdatabase-class.md) ve vašem kódu pro každou databázi, kterou chcete otevřít.|Základní sada záznamů objekty na databázových objektů.|Databázový objekt poskytuje rozhraní ke zdroji dat.|
|Vytvoření vazby datových sloupců do sady záznamů dynamicky.|V rozhraní ODBC přidejte kód do vaší třídy odvozené sady záznamů ke správě vazby. Přečtěte si článek [sada záznamů: Dynamické vazby datových sloupců (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||

## <a name="see-also"></a>Viz také:

[Sestavení na základě rozhraní .NET Framework](../mfc/building-on-the-framework.md)<br/>
[Posloupnost operací při sestavování aplikací MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Posloupnost operací při vytváření aplikací OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[Posloupnost operací při vytváření ovládacích prvků ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)
