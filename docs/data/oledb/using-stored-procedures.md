---
title: Použití uložených procedur | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: 062384713e0668965f9d04dc8f6907b05ac2bc89
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076877"
---
# <a name="using-stored-procedures"></a>Použití uložených procedur

Uložená procedura je spustitelný soubor objekt uložený v databázi. Volání uložené procedury se podobá vyvolání příkazu SQL. Použití uložených procedur na zdroj dat (namísto spuštění nebo při přípravě příkazu v klientské aplikaci), můžete zadat několik výhod, včetně vyšší výkon, nároky na omezenou síť a zlepšení konzistence a přesnost.

Uloženou proceduru mohou mít libovolný počet (včetně nuly) vstupní nebo výstupní parametry a můžete předat návratovou hodnotu. Můžete buď hodnoty parametrů pevný kód jako hodnoty dat, nebo použijte parametr značky (otazník "?").

> [!NOTE]
>  Uložené procedury, které jsou vytvořené pomocí jazyka Visual C++, musí být kompilována s CLR SQL serveru `/clr:safe` – možnost kompilátoru.

Zprostředkovatel OLE DB pro SQL Server (SQLOLEDB) podporuje tyto mechanismy, které uložených procedur použijte vrátit data:

- Každý **vyberte** příkaz v postupu generuje sadu výsledků dotazu.

- Postup může vrátit data prostřednictvím výstupní parametry.

- Postup může mít návratový kód celého čísla.

> [!NOTE]
> Nelze použít uložené procedury pomocí zprostředkovatele OLE DB pro Jet protože tento zprostředkovatel nepodporuje uložené procedury; v řetězcích dotazů jsou povoleny pouze konstanty.

## <a name="see-also"></a>Viz také

[Práce s šablonami příjemců OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)