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
ms.openlocfilehash: ed9eeb8f5ef0d53846761062cf2c6575d2eaf9e6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213295"
---
# <a name="data-source-odbc"></a>Zdroj dat (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

V rámci databázových podmínek je zdrojem dat konkrétní sada dat, informace vyžadované pro přístup k těmto datům a umístění zdroje dat, který lze popsat pomocí názvu zdroje dat. Chcete-li pracovat s třídou [CDatabase](../../mfc/reference/cdatabase-class.md), zdroj dat musí být ten, který jste nakonfigurovali prostřednictvím Správce rozhraní ODBC (Open Database Connectivity). Příklady zdrojů dat zahrnují vzdálenou databázi běžící na Microsoft SQL Server v síti nebo v souboru Microsoft Access v místním adresáři. Z aplikace můžete získat přístup k libovolnému zdroji dat, pro který máte ovladač ODBC.

V aplikaci můžete mít v aplikaci aktivní jeden nebo více zdrojů dat, z nichž každý představuje objekt `CDatabase`. Můžete mít také více současných připojení k jakémukoli zdroji dat. V závislosti na nainstalovaných ovladačích a možnostech ovladačů rozhraní ODBC se můžete připojit ke vzdálenému zdroji dat i k místním zdrojům dat. Další informace o zdrojích dat a správci rozhraní ODBC najdete v tématu Správce [rozhraní](../../data/odbc/odbc-basics.md) ODBC a [rozhraní ODBC](../../data/odbc/odbc-administrator.md).

V následujících tématech se dozvíte více o zdrojích dat:

- [Zdroj dat: Správa připojení (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)

- [Zdroj dat: Stanovení schématu zdroje dat (rozhraní ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
