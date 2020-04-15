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
ms.openlocfilehash: 436c796b24b0fa498f2b3f45e848392635b22a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376031"
---
# <a name="using-stored-procedures"></a>Použití uložených procedur

Uložená procedura je spustitelný objekt uložený v databázi. Volání uložené procedury je podobné vyvolání příkazu SQL. Použití uložené procedury na zdroj dat (namísto provádění nebo přípravu příkazu v klientské aplikaci) může poskytnout několik výhod, včetně vyšší výkon, snížená režie sítě a lepší konzistence a přesnost.

Uložená procedura může mít libovolný počet (včetně nulových) vstupních nebo výstupních parametrů a může předat vrácenou hodnotu. Můžete buď hodnoty pevných kódů jako specifické hodnoty dat, nebo použít značku parametru (otazník '?').

> [!NOTE]
> CLR SQL Server uložené procedury vytvořené pomocí Visual `/clr:safe` C++ musí být zkompilovány s možností kompilátoru.

Zprostředkovatel OLE DB pro SQL Server (SQLOLEDB) podporuje následující mechanismy, které uložené procedury používají k vrácení dat:

- Každý **příkaz SELECT** v postupu generuje sadu výsledků.

- Postup může vrátit data prostřednictvím výstupních parametrů.

- Procedura může mít celé číslo návratový kód.

> [!NOTE]
> Uložené procedury nelze použít s zprostředkovatelem OLE DB pro Jet, protože tento zprostředkovatel nepodporuje uložené procedury; v řetězcích dotazu jsou povoleny pouze konstanty.

## <a name="see-also"></a>Viz také

[Práce se šablonami příjemce technologie OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
