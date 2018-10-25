---
title: ODBC a databázové třídy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9e179bf7570ba2ce53369d59c836e8accf91e8de
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057935"
---
# <a name="odbc-and-the-database-classes"></a>ODBC a databázové třídy

Třídy databází MFC ODBC zapouzdření volání funkcí rozhraní ODBC API by normálně provedete sami v členské funkce [CDatabase](../../mfc/reference/cdatabase-class.md) a [CRecordset](../../mfc/reference/crecordset-class.md) třídy. Například sekvence volání komplexní ODBC, vazba vrácených záznamů na umístění úložiště, zpracování chybové stavy a další operace jsou pro vás spravuje služba databázové třídy. V důsledku toho použijete výrazně jednodušší rozhraní třídy manipulovat s záznamů pomocí objektu sady záznamů.

> [!NOTE]
>  Zdroje dat rozhraní ODBC jsou přístupné prostřednictvím třídy knihovny MFC rozhraní ODBC, jak je popsáno v tomto tématu, nebo třídy knihovny MFC objekt DAO (Data Access).

I když databázové třídy zapouzdřují funkce ODBC, neposkytují mapování 1: 1 z rozhraní ODBC API funkcí. Databázové třídy poskytují vyšší úroveň abstrakce, modelovat po nalezení objekty přístup k datům v aplikaci Microsoft Access a Microsoft Visual Basicu. Další informace najdete v tématu [rozhraní ODBC a MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Viz také

[ODBC – základy](../../data/odbc/odbc-basics.md)