---
title: Použití uložených procedur
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
ms.openlocfilehash: a7e97781d245e236c57942db15d61080d6418cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209271"
---
# <a name="using-stored-procedures"></a>Použití uložených procedur

Uložená procedura je spustitelný objekt uložený v databázi. Volání uložené procedury je podobné vyvolání příkazu jazyka SQL. Použití uložených procedur na zdroji dat (místo spuštění nebo přípravy příkazu v klientské aplikaci) může poskytovat několik výhod, včetně vyššího výkonu, snížené síťové režie a lepší konzistence a přesnosti.

Uložená procedura může mít libovolný počet (včetně nuly) vstupních nebo výstupních parametrů a může předat návratovou hodnotu. Hodnoty parametrů pevného kódu můžete určit jako konkrétní hodnoty dat nebo použít značku parametru (otazník "?").

> [!NOTE]
>  CLR SQL Server uložené procedury vytvořené pomocí vizuálu C++ musí být kompilovány pomocí možnosti kompilátoru `/clr:safe`.

Zprostředkovatel OLE DB pro SQL Server (SQLOLEDB) podporuje následující mechanismy, které uložené procedury používají k vrácení dat:

- Každý příkaz **Select** v proceduře vygeneruje sadu výsledků dotazu.

- Procedura může vracet data prostřednictvím výstupních parametrů.

- Procedura může mít návratový kód typu Integer.

> [!NOTE]
> U poskytovatele OLE DB pro stroj Jet nelze použít uložené procedury, protože tento zprostředkovatel nepodporuje uložené procedury. v řetězcích dotazů jsou povoleny pouze konstanty.

## <a name="see-also"></a>Viz také

[Práce s šablonami příjemců OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
