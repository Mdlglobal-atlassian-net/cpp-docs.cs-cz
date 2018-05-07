---
title: Použití uložených procedur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e5b49daa44fc8c88316134915945ad7ee01bb81a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-stored-procedures"></a>Použití uložených procedur
Uložená procedura je spustitelný soubor objekt uložená v databázi. Volání uložené procedury je podobná vyvolání příkazu SQL. Použití uložených procedur ve zdroji dat (namísto spuštění nebo při přípravě příkazu v aplikaci klienta) poskytují několik výhod, včetně vyšší výkon, sníženou sítě režii a vylepšené konzistence a přesnost.  
  
 Uložené procedury mohou mít libovolný počet (včetně nula) vstupní nebo výstupní parametry a můžete předat návratovou hodnotu. Můžete buď hodnoty parametru pevného kódu jako hodnoty dat, nebo použijte parametr značky (otazník '?').  
  
> [!NOTE]
>  SQL Server CLR musí být zkompilovány uložené procedury vytvořený pomocí Visual C++ pomocí **/CLR: safe** – možnost kompilátoru.  
  
 Zprostředkovatel OLE DB pro SQL Server (SQLOLEDB) podporuje následující mechanismy, které uložené procedury použijte vrátit data:  
  
-   Každý příkaz SELECT v postupu generuje je sada výsledků dotazu.  
  
-   Postup může vrátit data prostřednictvím výstupní parametry.  
  
-   Postup může mít celé návratový kód.  
  
> [!NOTE]
>  Nemůžete použít uložené procedury pomocí zprostředkovatele OLE DB pro Jet vzhledem k tomu, že zprostředkovatel nepodporuje uložené procedury; v řetězcích dotazů jsou povoleny pouze konstanty.  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami příjemců OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)