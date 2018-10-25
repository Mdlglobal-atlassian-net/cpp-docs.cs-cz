---
title: 'Zdroj dat: Stanovení schématu zdroje dat (ODBC) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b5ba9789226e54c9607e85caaa5e8af3f157f02d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052635"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Zdroj dat: Stanovení schématu zdroje dat (rozhraní ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

K nastavení datové členy ve vaší `CRecordset` objekty, je potřeba vědět schématu zdroje dat, ke kterému se připojujete. Stanovení schématu zdroje dat zahrnuje získání seznamu tabulek ve zdroji dat, seznam sloupců v každé tabulce, datový typ jednotlivých sloupců a existenci žádné indexy.

## <a name="see-also"></a>Viz také

[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Zdroj dat: Správa připojení (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)