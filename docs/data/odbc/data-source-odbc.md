---
title: Zdroj dat (ODBC) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6ad24a7be5c46c8019b22629003306ea99c56fd3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106954"
---
# <a name="data-source-odbc"></a>Zdroj dat (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.  
  
Zdroj dat v databázi podmínky, je konkrétní sady dat, informace požadované pro přístup k datům a umístění zdroje dat, které mohou být popsány pomocí názvu zdroje dat. Pro práci s třídou [CDatabase](../../mfc/reference/cdatabase-class.md), zdroj dat musí být ten, který jste nakonfigurovali prostřednictvím Správce připojení ODBC (Open Database). Příklady zdrojů dat patří vzdálené databáze, které běží na systému Microsoft SQL Server po síti nebo v místním adresáři souboru aplikace Microsoft Access. Z vaší aplikace můžete použít libovolný zdroj dat, pro který máte ovladač rozhraní ODBC.  
  
Můžete mít jednoho nebo více zdrojů dat v aplikaci najednou aktivní, každá `CDatabase` objektu. Také můžete mít více současných připojení k libovolnému zdroji dat. Můžete připojit na vzdálený stejně jako na místní zdroje dat, v závislosti na ovladače, které jste si nainstalovali a možnosti ovladače rozhraní ODBC. Další informace o zdrojích dat a správce rozhraní ODBC naleznete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [správce rozhraní ODBC](../../data/odbc/odbc-administrator.md).  
  
Následující témata popisují informace o zdrojích dat:  
  
- [Zdroj dat: Správa připojení (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)  
  
- [Zdroj dat: Stanovení schématu zdroje dat (rozhraní ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)  
  
## <a name="see-also"></a>Viz také  

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)