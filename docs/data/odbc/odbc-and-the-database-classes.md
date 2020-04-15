---
title: ODBC a databázové třídy
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 6511aab9bb048882fe9c3398dd17f769eb16220c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320068"
---
# <a name="odbc-and-the-database-classes"></a>ODBC a databázové třídy

Třídy databáze ROZHRANÍ MFC ODBC zapouzdřují volání funkce rozhraní API ROZHRANÍ ODBC, která byste normálně vytvořili v členských funkcích tříd [CDatabase](../../mfc/reference/cdatabase-class.md) a [CRecordset.](../../mfc/reference/crecordset-class.md) Například složité sekvence volání ODBC, vazba vrácených záznamů do skladových míst, zpracování chybových stavů a další operace jsou spravovány za vás třídami databáze. V důsledku toho použijete podstatně jednodušší rozhraní třídy k manipulaci se záznamy prostřednictvím objektu sady záznamů.

> [!NOTE]
> Zdroje dat ROZHRANÍ ODBC jsou přístupné prostřednictvím tříd knihovny MFC ODBC, jak je popsáno v tomto tématu, nebo prostřednictvím tříd DAO (MFC Data Access Object).

Přestože třídy databáze zapouzdřují funkce rozhraní ODBC, neposkytují mapování rozhraní API rozhraní ODBC. Třídy databáze poskytují vyšší úroveň abstrakce, modelované podle objektů přístupu k datům nalezených v aplikacích Microsoft Access a Microsoft Visual Basic. Další informace naleznete v tématu [ODBC a MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Viz také

[Základy rozhraní ODBC](../../data/odbc/odbc-basics.md)
