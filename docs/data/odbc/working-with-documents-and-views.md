---
title: Práce s dokumenty a zobrazeními | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], documents
- MFC [C++], views
- views [C++], MFC
- documents [C++], MFC
ms.assetid: 349b142d-1c5a-4b99-9de4-241e41d3d2f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c3879c6a29f95cc908d12c0b899214b521f46686
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060440"
---
# <a name="working-with-documents-and-views"></a>Práce s dokumenty a zobrazeními

Knihovny Microsoft Foundation Classes (MFC) závisí na architektuře document/view – pro celou řadu jejích funkcí. Obvykle dokument uloží vaše data a zobrazení se zobrazí v rámci klientské oblasti okna rámce a spravuje interakci uživatele s daty. Zobrazení komunikuje s dokumentem získat a aktualizovat data. Můžete použít databázové třídy, rozhraní nebo bez něj.

Další informace o použití databázových tříd v rámci najdete v tématu [knihovny MFC: použití databázových tříd s dokumenty a zobrazeními](../../data/mfc-using-database-classes-with-documents-and-views.md).

Ve výchozím nastavení Průvodce aplikací MFC vytvoří kostru aplikace bez podpory databáze. Můžete ale vybrat možnosti, které zahrnují minimální podporu databáze nebo více úplnou podporu založené na formulářích. Další informace o možnosti Průvodce aplikací najdete v tématu [Podpora databáze, Průvodce aplikací knihovny MFC](../../mfc/reference/database-support-mfc-application-wizard.md).

Můžete také použít databázové třídy bez použití úplné document/view – architektura. Další informace najdete v tématu [knihovny MFC: použití třídy databáze bez dokumentů a zobrazení](../../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Viz také

[Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)