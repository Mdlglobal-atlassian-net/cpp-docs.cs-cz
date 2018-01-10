---
title: "Požadavky ovladače ODBC pro dynamické sady | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2c444cd8e8d13cca7d891dba92e881b8ca167bbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Požadavky ovladače ODBC pro dynamické sady
V databázové třídy MFC rozhraní ODBC jsou dynamické sady sady záznamů s dynamické vlastnosti; jejich zůstaly synchronizované se zdrojem dat určitými způsoby. Dynamické sady MFC (ale ne dopředné sady záznamů) vyžadují ovladače ODBC s přizpůsobením API úrovně 2. Pokud ovladač pro vaše [zdroj dat](../../data/odbc/data-source-odbc.md) vyhovuje API úrovně 1 nastavit, když můžete nadále používat snímky v aktualizovatelné i jen pro čtení a dopředné sady záznamů, ale ne dynamické sady. Ovladač úrovně 1 však může podporovat dynamické sady, pokud ji podporuje rozšířené načítání a kurzory řízené.  
  
 V terminologii rozhraní ODBC dynamické sady a snímky jsou označovány jako kurzory. Kurzor je mechanismus používaný pro udržování přehledu o pozici v sadě záznamů. Další informace o požadavcích ovladače pro dynamické sady najdete v tématu [dynamická sada](../../data/odbc/dynaset.md). Další informace o kurzory najdete v tématu [připojení ODBC (Open Database)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) SDK v dokumentaci k webu MSDN.  
  
> [!NOTE]
>  Ovladač ODBC pro aktualizovatelné sady záznamů, musí podporovat příkazy umístěných aktualizací nebo **:: SQLSetPos** funkce rozhraní API ODBC. Pokud jsou podporované, používá MFC **:: SQLSetPos** pro efektivitu. Pro snímky, případně můžete použít knihovny kurzor, který poskytuje vyžaduje podporu pro aktualizovatelné snímky (statické kurzory a příkazy umístěné aktualizace).  
  
## <a name="see-also"></a>Viz také  
 [ODBC – základy](../../data/odbc/odbc-basics.md)