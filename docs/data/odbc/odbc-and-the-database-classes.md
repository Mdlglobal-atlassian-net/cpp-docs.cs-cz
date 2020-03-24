---
title: ODBC a databázové třídy
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 7c69f49cbe233eb0782fdaa9767ea55f4d04203c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213167"
---
# <a name="odbc-and-the-database-classes"></a>ODBC a databázové třídy

Třídy databáze rozhraní ODBC knihovny MFC zapouzdřují volání funkcí rozhraní ODBC API, které byste normálně provedli v členských funkcích tříd [CDatabase](../../mfc/reference/cdatabase-class.md) a [CRecordset](../../mfc/reference/crecordset-class.md) . Například komplexní sekvence volání rozhraní ODBC, vazba vrácených záznamů do umístění úložiště, manipulaci s chybovými stavy a další operace jsou pro vás spravovány databázovými třídami. Výsledkem je, že použijete výrazně jednodušší rozhraní třídy pro manipulaci s záznamy prostřednictvím objektu sady záznamů.

> [!NOTE]
>  Zdroje dat ODBC jsou přístupné prostřednictvím tříd knihovny MFC rozhraní ODBC, jak je popsáno v tomto tématu, nebo prostřednictvím tříd DAO (Data Access Object) knihovny MFC.

I když třídy databáze zapouzdřují funkce ODBC, neposkytují mapování funkcí rozhraní ODBC API 1:1. Třídy databáze poskytují vyšší úroveň abstrakce, která je modelována po objektech pro přístup k datům nalezeným v aplikacích Microsoft Access a Microsoft Visual Basic. Další informace naleznete v tématu [rozhraní ODBC a MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Viz také

[ODBC – základy](../../data/odbc/odbc-basics.md)
