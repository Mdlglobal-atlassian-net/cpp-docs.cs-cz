---
title: ODBC a MFC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f4e90281b3202303fa95e44684f8250259d0d653
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="odbc-and-mfc"></a>Rozhraní ODBC a knihovna MFC
> [!NOTE]
>  Chcete-li použít databázové třídy MFC, musí mít příslušný ovladač ODBC pro zdroj dat. Nejnovější ovladač Microsoft ODBC pro SQL Server je [13 ovladač Microsoft ODBC pro SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=50420). Většina dodavatelů databáze zadejte ovladače ODBC pro Windows. 
  
 Toto téma představuje hlavní koncepty tříd databáze založené na rozhraní ODBC knihovny Microsoft Foundation třídy (MFC) a poskytuje přehled o fungování třídy společně. Další informace o rozhraní ODBC a MFC najdete v následujících tématech:  
  
-   [Připojení ke zdroji dat](connecting-to-a-data-source.md)  
  
-   [Výběr a manipulace s nimi záznamů](selecting-and-manipulating-records.md)  
  
-   [Zobrazení a manipulace dat ve formuláři](displaying-and-manipulating-data-in-a-form.md)  
  
-   [Práce s dokumenty a zobrazeními](working-with-documents-and-views.md)  
  
-   [Přístup k rozhraní ODBC a jazyku SQL](access-to-odbc-and-sql.md)  
  
-   [Další výklad o třídách knihovny MFC rozhraní ODBC](further-reading-about-the-mfc-odbc-classes.md)  
  
 Databázové třídy MFC založené na rozhraní ODBC jsou navržená k poskytování přístupu k jakékoli databázi, pro který je k dispozici ovladač ODBC. Protože třídy použití rozhraní ODBC, vaše aplikace může přistupovat k datům v mnoha různých datových formátů a různé konfigurace místní nebo vzdálené. Nemusíte psát zvláštní případ kód pro zpracování různých databázové systémy (systémy DBMS). Tak dlouho, dokud uživatelé mají odpovídající ovladače ODBC pro data, která chtějí získat přístup, budou pomocí programu k manipulaci s daty v tabulkách, které jsou v ní uloženy.  
  
## <a name="see-also"></a>Viz také  
 [Open Database Connectivity (ODBC)](open-database-connectivity-odbc.md)