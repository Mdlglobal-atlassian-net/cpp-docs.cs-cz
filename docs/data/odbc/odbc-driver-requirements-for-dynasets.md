---
title: Požadavky ovladače ODBC pro dynamické sady
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
ms.openlocfilehash: 3507a5ee7dcfb8bf4f4eee12ef9264c16ad904c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213106"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Požadavky ovladače ODBC pro dynamické sady

V třídách knihovny MFC rozhraní ODBC jsou dynamické sady sady záznamů s dynamickými vlastnostmi; v některých ohledech zůstanou synchronizované se zdrojem dat. Dynamické sady MFC (ale ne pouze dopředné sady záznamů) vyžadují ovladač ODBC s vyhovující úrovní rozhraní API úrovně 2. Pokud ovladač [zdroje dat](../../data/odbc/data-source-odbc.md) odpovídá sadě rozhraní API úrovně 1, můžete i nadále používat jen aktualizovatelné snímky i snímky jen pro čtení a pouze dopředné sady záznamů, ale ne dynamické sady. Ovladač úrovně 1 však může podporovat dynamické sady, pokud podporuje rozšířené načítání a kurzory řízené sadou klíčů.

V terminologii rozhraní ODBC jsou dynamické sady a snímky označovány jako kurzory. Kurzor je mechanismus, který slouží k udržení přehledu o pozici v sadě záznamů. Další informace o požadavcích na ovladače pro dynamické sady naleznete v tématu [dynamická sada](../../data/odbc/dynaset.md). Další informace o kurzorech naleznete v tématu sada SDK [rozhraní ODBC (Open Database Connectivity)](/sql/odbc/microsoft-open-database-connectivity-odbc) v dokumentaci MSDN.

> [!NOTE]
>  Pro aktualizovatelné sady záznamů musí váš ovladač ODBC podporovat buď příkazy umístěné v Update, nebo funkci `::SQLSetPos` rozhraní API ODBC. Pokud jsou podporovány obě, knihovna MFC používá `::SQLSetPos` pro efektivitu. Alternativně můžete pro snímky použít knihovnu kurzorů, která poskytuje požadovanou podporu pro aktualizovatelné snímky (statické kurzory a příkazy s umístěnými aktualizacemi).

## <a name="see-also"></a>Viz také

[ODBC – základy](../../data/odbc/odbc-basics.md)
