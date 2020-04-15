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
ms.openlocfilehash: 38a625c73a17ecae4d8adc61e8c56bc4bdda67f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320074"
---
# <a name="odbc-and-mfc"></a>Rozhraní ODBC a knihovna MFC

> [!NOTE]
> Chcete-li použít třídy databáze knihovny MFC, musíte mít pro zdroj dat příslušný ovladač ODBC. Posledním posledním ovladačem odhlašení ODBC pro SQL Server je [ovladač OdBC 13 pro SQL Server](https://www.microsoft.com/download/details.aspx?id=50420). Většina dodavatelů databáze poskytuje ovladač ODBC pro systém Windows.

Toto téma představuje hlavní koncepty knihovny Microsoft Foundation Classes (MFC) databáze odbc tříd a poskytuje přehled o tom, jak třídy spolupracují. Další informace o rozhraníCH ODBC a knihovně MFC naleznete v následujících tématech:

- [Připojení ke zdroji dat](connecting-to-a-data-source.md)

- [Výběr a manipulace se záznamy](selecting-and-manipulating-records.md)

- [Zobrazení a manipulace s daty ve formuláři](displaying-and-manipulating-data-in-a-form.md)

- [Práce s dokumenty a zobrazeními](working-with-documents-and-views.md)

- [Přístup k rozhraní ODBC a jazyku SQL](access-to-odbc-and-sql.md)

- [Další výklad o třídách knihovny MFC rozhraní ODBC](further-reading-about-the-mfc-odbc-classes.md)

Třídy databáze knihovny MFC založené na rozhraní ODBC jsou navrženy tak, aby poskytovaly přístup k libovolné databázi, pro kterou je k dispozici ovladač ROZHRANÍ ODBC. Vzhledem k tomu, že třídy používají rozhraní ODBC, může aplikace přistupovat k datům v mnoha různých formátech dat a v různých místních/vzdálených konfiguracích. Není třeba psát kód zvláštní případ pro zpracování různých systémů pro správu databáze (DBMS). Pokud mají uživatelé vhodný ovladač ODBC pro data, ke kterým chtějí získat přístup, mohou pomocí programu manipulovat s daty v tamu uložených tabulkách.

## <a name="see-also"></a>Viz také

[Připojení k otevřené databázi (ODBC)](open-database-connectivity-odbc.md)
