---
title: "Posloupnost operací při vytváření databázových aplikací | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f3403807e38f59abc68bf93f510476951c5ec8ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>Posloupnost operací při vytváření databázových aplikací
Následující tabulka uvádí vaše role a role rozhraní framework zápis databázových aplikací.  
  
> [!NOTE]
>  Prostředí Visual C++ a průvodců nepodporují rozhraní DAO (i když jsou zahrnuté třídy DAO a můžete je dál používat). Společnost Microsoft doporučuje použití rozhraní ODBC pro nové projekty MFC. DAO byste měli používat jenom pro údržbu existujících aplikací.  
  
### <a name="creating-database-applications"></a>Vytváření databázových aplikací  
  
|Úloha|Můžete provést|Nepodporuje rozhraní|  
|----------|------------|------------------------|  
|Rozhodněte, jestli použít třídy knihovny MFC rozhraní ODBC a DAO.|Použití pro nové projekty MFC rozhraní ODBC. Pomocí rozhraní DAO pouze zachovat stávající aplikace. Obecné informace najdete v článku [programovací přístup dat](../data/data-access-programming-mfc-atl.md).|Rozhraní framework poskytuje třídy, které podporují přístup k databázi.|  
|Vytvoření kostru aplikace s možnosti databáze.|Spusťte Průvodce aplikací MFC. Vyberte možnosti na stránce Podpora databáze. Pokud zvolíte možnost, která vytvoří zobrazení záznamu, také zadejte:<br /><br /> -Data zdroje a název tabulky nebo názvy<br />-Dotaz na název nebo názvy.|Průvodce aplikací MFC vytvoří soubory a určuje, že obsahuje nezbytné. V závislosti na možnostech, které zadáte může zahrnovat soubory třídy sady záznamů.|  
|Návrh formuláře databáze nebo formulářů.|Použití editoru dialogových oken Visual C++ umístit ovládacími prvky v dialogovém okně Šablony prostředky pro vaše tříd zobrazení záznamu.|Průvodce aplikací MFC vytvoří prostředek dialogové okno prázdné šablonu můžete vyplnit.|  
|Vytvořte další záznam třídy zobrazení a sady záznamů podle potřeby.|Zobrazení tříd použijte k vytvoření třídy a dialogové okno editor k zobrazení návrhu.|Zobrazení tříd vytvoří další soubory pro nové třídy.|  
|Vytvořte sadu záznamů objekty podle potřeby v kódu. Použijte jednotlivých záznamů k manipulaci s záznamy...|Vaše sady záznamů jsou založené na třídy odvozené z [CRecordset](../mfc/reference/crecordset-class.md) pomocí průvodců.|Rozhraní ODBC používá pole záznamu (exchange – RFX) pro výměnu dat mezi databází a sady záznamů pole datových členů. Pokud používáte zobrazení záznamů, výměna dialogových dat (DDX) výměny dat mezi ovládacími prvky v zobrazení záznamů a záznamů.|  
|.. nebo vytvořit explicitního [CDatabase](../mfc/reference/cdatabase-class.md) ve vašem kódu pro každou databázi, kterou chcete otevřít.|Základní vašich objektů sady záznamů pro databázové objekty.|Objekt databáze poskytuje rozhraní ke zdroji dat.|  
|Dynamicky vazby datových sloupců do sady záznamů.|V rozhraní ODBC přidávání kódu do vaší třídy odvozené sady záznamů ke správě vazby. Najdete v článku [sada záznamů: dynamické vazby datových sloupců (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||  
  
## <a name="see-also"></a>Viz také  
 [Vytváření v rozhraní Framework](../mfc/building-on-the-framework.md)   
 [Posloupnost operací při sestavování aplikací MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Posloupnost operací při vytváření aplikací OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Posloupnost operací při vytváření ovládacích prvků ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)
