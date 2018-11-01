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
ms.openlocfilehash: 7c7540528bed2499ed9dfb09ed39658914c81e14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560625"
---
# <a name="odbc-and-mfc"></a>Rozhraní ODBC a knihovna MFC

> [!NOTE]
>  Pokud chcete použít databázové třídy knihovny MFC, musí mít odpovídající ovladač ODBC pro zdroj dat. Nejnovější ovladač Microsoft ODBC pro SQL Server je [13 ovladač Microsoft ODBC pro SQL Server](https://www.microsoft.com/download/details.aspx?id=50420). Většina dodavatelů databáze poskytuje ovladač rozhraní ODBC pro Windows.

Toto téma představuje hlavní koncepty tříd databázi založenou na ODBC knihovny Microsoft Foundation Classes (MFC) a poskytuje přehled o fungování třídy dohromady. Další informace o rozhraní ODBC a MFC naleznete v následujících tématech:

- [Připojení ke zdroji dat](connecting-to-a-data-source.md)

- [Výběr záznamů a manipulace s nimi](selecting-and-manipulating-records.md)

- [Zobrazení dat ve formuláři a manipulace s nimi](displaying-and-manipulating-data-in-a-form.md)

- [Práce s dokumenty a zobrazeními](working-with-documents-and-views.md)

- [Přístup k rozhraní ODBC a jazyku SQL](access-to-odbc-and-sql.md)

- [Další výklad o třídách knihovny MFC rozhraní ODBC](further-reading-about-the-mfc-odbc-classes.md)

Databázových tříd MFC založených na rozhraní ODBC jsou navržené pro poskytování přístupu k jakékoli databázi, pro který je k dispozici ovladač rozhraní ODBC. Protože třídy použití rozhraní ODBC, vaše aplikace můžou k datům v mnoha různých datových formátů a různé konfigurace místní/vzdálené. Není nutné napsat kód zvláštní případy zpracovat různé systémy správy databáze (DBMS). Tak dlouho, dokud mají vaši uživatelé příslušný ovladač ODBC pro data, která chtějí získat přístup, použitím programu pro manipulaci s daty v tabulkách v ní uloženy.

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](open-database-connectivity-odbc.md)