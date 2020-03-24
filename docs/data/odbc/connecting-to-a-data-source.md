---
title: Připojení ke zdroji dat
ms.date: 11/04/2016
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
ms.openlocfilehash: 712910aca2622f2678b8b9d06b18a2fdbf9157e4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213340"
---
# <a name="connecting-to-a-data-source"></a>Připojení ke zdroji dat

Zdroj dat ODBC je konkrétní sada dat, informace vyžadované pro přístup k těmto datům a umístění zdroje dat, který lze popsat pomocí názvu zdroje dat. Zdroj dat z pohledu vašeho programu zahrnuje data, systém DBMS, síť (pokud existuje) a rozhraní ODBC.

Aby bylo možné získat přístup k datům poskytovaným zdrojem dat, musí nejdřív navázat spojení se zdrojem dat. Veškerý přístup k datům je spravován prostřednictvím tohoto připojení.

Připojení ke zdroji dat jsou zapouzdřena třídou [CDatabase](../../mfc/reference/cdatabase-class.md). Když je objekt `CDatabase` připojen ke zdroji dat, můžete:

- Sestavujte [sady záznamů](../../mfc/reference/crecordset-class.md), které v tabulkách nebo dotazech vybírají záznamy.

- Spravujte [transakce](../../data/odbc/transaction-odbc.md), dávkové aktualizace tak, aby všechny byly potvrzeny na zdroj dat najednou (nebo celá transakce je vrácena zpět, takže zdroj dat je nezměněný) – Pokud zdroj dat podporuje požadovanou úroveň transakcí.

- Přímo spustit příkazy [SQL](../../data/odbc/sql.md) .

Po dokončení práce s připojením ke zdroji dat zavřete objekt `CDatabase` a buď jej odstraňte, nebo ho znovu použijte pro nové připojení. Další informace o připojeních ke zdroji dat najdete v tématu [zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md).

## <a name="see-also"></a>Viz také

[Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)
