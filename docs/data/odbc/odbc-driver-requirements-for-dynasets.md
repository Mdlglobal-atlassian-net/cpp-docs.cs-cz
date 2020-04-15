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
ms.openlocfilehash: c612e8ea91882a6e744a8f47afe0decbeba85358
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367205"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Požadavky ovladače ODBC pro dynamické sady

V databázových třídách Knihovny MFC ODBC jsou dynamické sady s dynamickými vlastnostmi. zůstávají synchronizovány se zdrojem dat určitými způsoby. Dynasady knihovny MFC (nikoli však pouze předsuňkované sady záznamů) vyžadují ovladač ROZHRANÍ ODBC s shodou rozhraní API úrovně 2. Pokud ovladač pro [váš zdroj dat](../../data/odbc/data-source-odbc.md) odpovídá sadě rozhraní API úrovně 1, můžete stále používat aktualizovatelné snímky i snímky jen pro čtení a sady záznamů pouze pro předávání, ale ne dynamické sady. Ovladač úrovně 1 však může podporovat dynasady, pokud podporuje rozšířené načítání a kurzory řízené sadou klíčů.

V terminologii ODBC jsou dynasady a snímky označovány jako kurzory. Kurzor je mechanismus používaný pro sledování jeho pozice v sadě záznamů. Další informace o požadavcích ovladačů pro dynasety naleznete [v tématu Dynaset](../../data/odbc/dynaset.md). Další informace o kurzorech naleznete v souboru SDK [open database connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) v dokumentaci k msdn.

> [!NOTE]
> U aktualizovatelných sad záznamů musí ovladač ROZHRANÍ ODBC `::SQLSetPos` podporovat buď umístěné příkazy aktualizace, nebo funkci rozhraní API ROZHRANÍ ODBC. Pokud jsou podporovány obě, knihovna MFC používá `::SQLSetPos` pro efektivitu. Případně pro snímky můžete použít knihovnu kurzorů, která poskytuje požadovanou podporu pro aktualizovatelné snímky (statické kurzory a příkazy umístěné aktualizace).

## <a name="see-also"></a>Viz také

[Základy rozhraní ODBC](../../data/odbc/odbc-basics.md)
