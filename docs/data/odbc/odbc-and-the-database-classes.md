---
title: "ODBC a databázové třídy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e3041a4fc027a8786fb62db7df6eaf486633ce97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-and-the-database-classes"></a>ODBC a databázové třídy
Databázové třídy MFC rozhraní ODBC pro zapouzdření volání funkcí rozhraní API ODBC by za normálních okolností provedete sami v člen funkce [CDatabase](../../mfc/reference/cdatabase-class.md) a [CRecordset](../../mfc/reference/crecordset-class.md) třídy. Například komplexní pořadí volání rozhraní ODBC, vazba vrácené záznamy na umístění úložiště, zpracování chybové stavy a další operace jsou pro vás spravuje služba databázové třídy. V důsledku toho použijte výrazně jednodušší třídy rozhraní k manipulaci s záznamy prostřednictvím objekt sady záznamů.  
  
> [!NOTE]
>  Zdroje dat ODBC jsou přístupné prostřednictvím třídy knihovny MFC rozhraní ODBC, jak je popsáno v tomto tématu nebo třídy MFC objekt DAO (Data Access).  
  
 I když databázové třídy zapouzdřují fungování rozhraní ODBC, neposkytují mapování 1: 1 funkcí rozhraní API ODBC. Databázové třídy poskytují vyšší úrovni abstrakce modelovány po nalezeny objekty přístup k datům v aplikaci Microsoft Access a Microsoft Visual Basic. Další informace najdete v tématu [rozhraní ODBC a MFC](../../data/odbc/odbc-and-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [ODBC – základy](../../data/odbc/odbc-basics.md)