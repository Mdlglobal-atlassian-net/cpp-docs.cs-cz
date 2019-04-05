---
title: 'Zdroj dat: Stanovení schématu zdroje dat (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
ms.openlocfilehash: c419a3ac2d870e6a85675492ee6c9b726427a0e9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040027"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Zdroj dat: Stanovení schématu zdroje dat (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

K nastavení datové členy ve vaší `CRecordset` objekty, je potřeba vědět schématu zdroje dat, ke kterému se připojujete. Stanovení schématu zdroje dat zahrnuje získání seznamu tabulek ve zdroji dat, seznam sloupců v každé tabulce, datový typ jednotlivých sloupců a existenci žádné indexy.

## <a name="see-also"></a>Viz také:

[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Zdroj dat: Správa připojení (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)