---
title: ODBC a databázové třídy
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 7692a8128e3dac97c9107e986f6698db76c22c58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395830"
---
# <a name="odbc-and-the-database-classes"></a>ODBC a databázové třídy

Třídy databází MFC ODBC zapouzdření volání funkcí rozhraní ODBC API by normálně provedete sami v členské funkce [CDatabase](../../mfc/reference/cdatabase-class.md) a [CRecordset](../../mfc/reference/crecordset-class.md) třídy. Například sekvence volání komplexní ODBC, vazba vrácených záznamů na umístění úložiště, zpracování chybové stavy a další operace jsou pro vás spravuje služba databázové třídy. V důsledku toho použijete výrazně jednodušší rozhraní třídy manipulovat s záznamů pomocí objektu sady záznamů.

> [!NOTE]
>  Zdroje dat rozhraní ODBC jsou přístupné prostřednictvím třídy knihovny MFC rozhraní ODBC, jak je popsáno v tomto tématu, nebo třídy knihovny MFC objekt DAO (Data Access).

I když databázové třídy zapouzdřují funkce ODBC, neposkytují mapování 1: 1 z rozhraní ODBC API funkcí. Databázové třídy poskytují vyšší úroveň abstrakce, modelovat po nalezení objekty přístup k datům v aplikaci Microsoft Access a Microsoft Visual Basicu. Další informace najdete v tématu [rozhraní ODBC a MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Viz také:

[ODBC – základy](../../data/odbc/odbc-basics.md)