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
ms.openlocfilehash: 3ba333b8c5c90a4b9bb1aca94f57e5fc92aa2b47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647054"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Požadavky ovladače ODBC pro dynamické sady

Třídy databází MFC ODBC dynamické sady jsou sady záznamů s dynamické vlastnosti; zůstaly synchronizované se zdrojem dat určitým způsobem. Dynamické knihovny MFC (ale ne pouze vpřed) vyžadují ovladač rozhraní ODBC s přizpůsobením API úrovně 2. Pokud ovladač pro vaše [zdroj dat](../../data/odbc/data-source-odbc.md) odpovídá API úrovně 1 nastavení, můžete stále použít snímky aktualizovatelné i jen pro čtení a pouze vpřed, ale ne dynamické sady. Ale ovladače úrovně 1 může podporovat dynamické sady podporuje rozšířené načítání a kurzory řízené.

V terminologii rozhraní ODBC snímky a dynamické sady jsou označovány jako ukazatele. Kurzor je mechanismus používaný pro uchování záznamu o jeho pozice v sadě záznamů. Další informace o požadavcích na ovladače pro dynamické sady najdete v tématu [dynamická sada](../../data/odbc/dynaset.md). Další informace o kurzory, najdete v článku [připojení ODBC (Open Database)](/previous-versions/windows/desktop/ms710252) sady SDK v dokumentaci MSDN.

> [!NOTE]
>  Pro aktualizovatelné sady záznamů, ovladač rozhraní ODBC musí podporovat příkazy umístěných aktualizací nebo `::SQLSetPos` funkce ODBC API. Pokud jsou podporované, knihovna MFC používá `::SQLSetPos` efektivitu. Pro snímky, můžete alternativně použít knihovna kurzorů rozhraní, které poskytuje vyžaduje podporu pro aktualizovatelné (statický kurzor a příkazy umístěné aktualizace).

## <a name="see-also"></a>Viz také

[ODBC – základy](../../data/odbc/odbc-basics.md)