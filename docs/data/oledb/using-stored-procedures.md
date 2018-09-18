---
title: Použití uložených procedur | Dokumentace Microsoftu
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
ms.openlocfilehash: f7b68e7494303e06245a713abc8f1d6e0424773e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114641"
---
# <a name="using-stored-procedures"></a>Použití uložených procedur

Uložená procedura je spustitelný soubor objekt uložený v databázi. Volání uložené procedury se podobá vyvolání příkazu SQL. Použití uložených procedur na zdroj dat (namísto spuštění nebo při přípravě příkazu v klientské aplikaci), můžete zadat několik výhod, včetně vyšší výkon, nároky na omezenou síť a zlepšení konzistence a přesnost.  
  
Uloženou proceduru mohou mít libovolný počet (včetně nuly) vstupní nebo výstupní parametry a můžete předat návratovou hodnotu. Můžete buď hodnoty parametrů pevný kód jako hodnoty dat, nebo použijte parametr značky (otazník "?").  
  
> [!NOTE]
>  Uložené procedury, které jsou vytvořené pomocí jazyka Visual C++, musí být kompilována s CLR SQL serveru `/clr:safe` – možnost kompilátoru.  
  
Zprostředkovatel OLE DB pro SQL Server (SQLOLEDB) podporuje tyto mechanismy, které uložených procedur použijte vrátit data:  
  
- Každý příkaz SELECT v postupu generuje sadu výsledků dotazu.  
  
- Postup může vrátit data prostřednictvím výstupní parametry.  
  
- Postup může mít návratový kód celého čísla.  
  
> [!NOTE]
>  Nelze použít uložené procedury pomocí zprostředkovatele OLE DB pro Jet protože tento zprostředkovatel nepodporuje uložené procedury; v řetězcích dotazů jsou povoleny pouze konstanty.  
  
## <a name="see-also"></a>Viz také  

[Práce s šablonami příjemců OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)