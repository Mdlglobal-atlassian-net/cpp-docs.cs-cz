---
title: Zdroj dat (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
ms.openlocfilehash: b435c65bab565e109d37e1dd24e051993cbb30c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397910"
---
# <a name="data-source-odbc"></a>Zdroj dat (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Zdroj dat v databázi podmínky, je konkrétní sady dat, informace požadované pro přístup k datům a umístění zdroje dat, které mohou být popsány pomocí názvu zdroje dat. Pro práci s třídou [CDatabase](../../mfc/reference/cdatabase-class.md), zdroj dat musí být ten, který jste nakonfigurovali prostřednictvím Správce připojení ODBC (Open Database). Příklady zdrojů dat patří vzdálené databáze, které běží na systému Microsoft SQL Server po síti nebo v místním adresáři souboru aplikace Microsoft Access. Z vaší aplikace můžete použít libovolný zdroj dat, pro který máte ovladač rozhraní ODBC.

Můžete mít jednoho nebo více zdrojů dat v aplikaci najednou aktivní, každá `CDatabase` objektu. Také můžete mít více současných připojení k libovolnému zdroji dat. Můžete připojit na vzdálený stejně jako na místní zdroje dat, v závislosti na ovladače, které jste si nainstalovali a možnosti ovladače rozhraní ODBC. Další informace o zdrojích dat a správce rozhraní ODBC naleznete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [správce rozhraní ODBC](../../data/odbc/odbc-administrator.md).

Následující témata popisují informace o zdrojích dat:

- [Zdroj dat: Správa připojení (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)

- [Zdroj dat: Stanovení schématu zdroje dat (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)

## <a name="see-also"></a>Viz také:

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)