---
title: Rozhraní ODBC a knihovna MFC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
ms.openlocfilehash: 94a3455324a52b789bcfcf192b698a3c42b37c00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213161"
---
# <a name="odbc-and-mfc"></a>Rozhraní ODBC a knihovna MFC

> [!NOTE]
>  Chcete-li použít třídy databáze knihovny MFC, je nutné mít vhodný ovladač ODBC pro váš zdroj dat. Poslední ovladač Microsoft ODBC pro SQL Server je [ovladač Microsoft ODBC Driver 13 pro SQL Server](https://www.microsoft.com/download/details.aspx?id=50420). Většina dodavatelů databáze poskytuje ovladač ODBC pro Windows.

Toto téma představuje hlavní koncepty databázových tříd založených na rozhraní ODBC knihovny MFC (Microsoft Foundation Classes) a poskytuje přehled o tom, jak třídy spolupracují. Další informace o rozhraní ODBC a knihovně MFC naleznete v následujících tématech:

- [Připojení ke zdroji dat](connecting-to-a-data-source.md)

- [Výběr záznamů a manipulace s nimi](selecting-and-manipulating-records.md)

- [Zobrazení dat ve formuláři a manipulace s nimi](displaying-and-manipulating-data-in-a-form.md)

- [Práce s dokumenty a zobrazeními](working-with-documents-and-views.md)

- [Přístup k rozhraní ODBC a jazyku SQL](access-to-odbc-and-sql.md)

- [Další výklad o třídách knihovny MFC rozhraní ODBC](further-reading-about-the-mfc-odbc-classes.md)

Databázové třídy knihovny MFC založené na rozhraní ODBC jsou navržené tak, aby poskytovaly přístup k libovolné databázi, pro kterou je k dispozici ovladač ODBC. Vzhledem k tomu, že třídy používají rozhraní ODBC, může vaše aplikace přistupovat k datům v mnoha různých datových formátech a v různých místních/vzdálených konfiguracích. Nemusíte psát speciální kód pro zpracování různých systémů správy databáze (DBMS). Pokud mají vaši uživatelé vhodný ovladač ODBC pro data, ke kterým chtějí získat přístup, můžou pomocí programu manipulovat s daty v tabulkách, které jsou tam uložené.

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](open-database-connectivity-odbc.md)
