---
title: ODBC – třídy a vlákna
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: 8cb5df605bef31e177e976798f975bb4ca14ced7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213160"
---
# <a name="odbc-classes-and-threads"></a>ODBC – třídy a vlákna

Počínaje knihovnou MFC 4,2 existuje podpora více vláken pro třídy knihovny MFC rozhraní ODBC. Upozorňujeme však, že knihovna MFC neposkytuje podporu multithreadingu pro třídy DAO.

Podpora multithreadingu pro třídy rozhraní ODBC má určitá omezení. Vzhledem k tomu, že tyto třídy zabalí rozhraní API rozhraní ODBC, jsou omezeny na podporu multithreadingu komponent, na kterých jsou sestaveny. Například mnohé ovladače ODBC nejsou bezpečné pro přístup z více vláken; Proto třídy knihovny MFC rozhraní ODBC nejsou bezpečné pro přístup z více vláken, pokud je použijete s jedním z těchto ovladačů. Měli byste ověřit, jestli je váš konkrétní ovladač bezpečný pro přístup z více vláken.

Při vytváření vícevláknové aplikace byste měli být velmi opatrní v používání více vláken pro manipulaci se stejným objektem. Například použití stejného objektu `CRecordset` ve dvou vláknech může způsobit problémy při načítání dat; operace načtení v jednom vlákně může přepsat data načtená v jiném vlákně. Častěji použití tříd knihovny MFC rozhraní ODBC v samostatných vláknech je sdílení otevřeného objektu `CDatabase` napříč vlákny pro použití stejného připojení rozhraní ODBC, se samostatným objektem `CRecordset` v každém vlákně. Všimněte si, že byste neměli předávat neotevřený `CDatabase` objekt objektu `CRecordset` v jiném vlákně.

> [!NOTE]
>  Pokud potřebujete více vláken manipulovat se stejným objektem, měli byste implementovat příslušné synchronizační mechanismy, například důležité oddíly. Uvědomte si, že některé operace, například `Open`, nejsou chráněné. Měli byste se ujistit, že tyto operace nebudou volány souběžně z různých vláken.

Další informace o vytváření vícevláknových aplikací naleznete v tématu témata s více [vlákny](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Programování přístupu k datům (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
