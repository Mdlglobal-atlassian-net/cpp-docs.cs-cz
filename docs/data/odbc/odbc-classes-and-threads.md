---
title: ODBC – třídy a vlákna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab115db1387adb71a69b735d676fa657d370752f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052470"
---
# <a name="odbc-classes-and-threads"></a>ODBC – třídy a vlákna

Od verze 4.2 knihovny MFC, je podpora více vláken ve třídách knihovny MFC rozhraní ODBC. Upozorňujeme však, že MFC neposkytuje podpora více vláken pro třídy DAO.

Multithreading podpora ODBC – třídy má určitá omezení. Protože tyto třídy zabalení rozhraní ODBC API, jsou omezeny na podpoře multithreadingu komponenty, na kterých jsou vytvořeny. Například mnoho ovladačů ODBC nejsou bezpečné pro vlákna; třídy knihovny MFC rozhraní ODBC proto nejsou bezpečné pro vlákna je-li použít s jednou z těchto ovladačů. Měli byste ověřit, jestli konkrétní ovladač je bezpečná pro vlákno.

Při vytváření aplikace s více vlákny, byste měli být opatrní při použití více vláken k manipulaci s na stejný objekt. Například pomocí stejných `CRecordset` objektu ve dvou vláken může způsobit problémy při načítání dat; operaci načtení v jednom vlákně může přepsat dat načtené v jiném vlákně. Běžnější použití tříd knihovny MFC rozhraní ODBC v samostatných vláknech je sdílet otevřenou `CDatabase` objektu napříč vlákny pomocí stejného připojení rozhraní ODBC se samostatným `CRecordset` objektu v každém vlákně. Všimněte si, že by neměla předat neotevřených `CDatabase` do objektu `CRecordset` objektu v jiném vlákně.

> [!NOTE]
>  Pokud potřebujete více vláken, manipulaci s na stejný objekt, měli byste implementovat mechanismy příslušné synchronizace, jako je například kritické oddíly. Mějte na paměti, který některé operace, jako například `Open`, nejsou chráněné. Měli byste si být jisti, že tyto operace nebudou současně volat ze samostatných vláknech.

Další informace o vytváření aplikací s více vlákny, naleznete v tématu [Témata multithreadingu](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Přístup k datům programování knihovny MFC nebo ATL)](../../data/data-access-programming-mfc-atl.md)