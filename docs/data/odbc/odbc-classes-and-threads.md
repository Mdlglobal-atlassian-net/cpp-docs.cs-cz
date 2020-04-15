---
title: ODBC – třídy a vlákna
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: aaf54a3a1d616cde5742dad45955bd415f612d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368692"
---
# <a name="odbc-classes-and-threads"></a>ODBC – třídy a vlákna

Počínaje knihovnou MFC 4.2 je podpora více vláken pro třídy Knihovny MFC ODBC. Všimněte si však, že knihovna MFC neposkytuje podporu více vláken pro třídy DAO.

Podpora více vláken pro třídy ODBC má určitá omezení. Protože tyto třídy zabalit ROZHRANÍ API ROZHRANÍ ODBC, jsou omezeny na podporu více vláken součásti, na kterých jsou postaveny. Například mnoho ovladačů ODBC není bezpečné pro přístup z více vláken; Proto třídy Rozhraní MFC ODBC nejsou bezpečné pro přístup z více vláken, pokud je používáte s jedním z těchto ovladačů. Měli byste ověřit, zda je váš konkrétní ovladač bezpečný pro přístup z více vláken.

Při vytváření vícevláknové aplikace byste měli být velmi opatrní při použití více vláken k manipulaci se stejným objektem. Například použití stejného `CRecordset` objektu ve dvou vláknech může způsobit problémy při načítání dat; operace načtení v jednom vlákně může přepsat data načtená v druhém vlákně. Běžnější použití tříd knihovny MFC ODBC v samostatných `CDatabase` vláknech je sdílení otevřeného objektu mezi `CRecordset` vlákny a použití stejného připojení ODBC se samostatným objektem v každém vlákně. Všimněte si, že byste `CDatabase` neměli `CRecordset` předat neotevřený objekt objektu v jiném vlákně.

> [!NOTE]
> Pokud musíte mít více vláken manipulovat se stejným objektem, měli byste implementovat příslušné synchronizační mechanismy, jako jsou kritické oddíly. Uvědomte si, že `Open`některé operace, například , nejsou chráněny. Měli byste si být jisti, že tyto operace nebudou volány souběžně ze samostatných vláken.

Další informace o vytváření vícevláknových aplikací naleznete v [tématu Témata s více vlákny](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Viz také

[Připojení k otevřené databázi (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Programování přístupu k datům (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
