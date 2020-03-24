---
title: Definování uložených procedur
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
ms.openlocfilehash: 9bab086bf6982eae5779d3199cfd2ac2c8efe77f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211001"
---
# <a name="defining-stored-procedures"></a>Definování uložených procedur

Před voláním uložené procedury je nutné ji nejprve definovat pomocí makra [DEFINE_COMMAND](../../data/oledb/define-command.md) . Při definování příkazu je třeba zadat parametry s otazníkem (?) jako značku parametru:

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{INSERT {name, phone} INTO shippers (?,?)}"))
```

Syntaxe (použití závorek atd.) použitá v příkladech kódu v tomto tématu je specifická pro SQL Server. Syntaxe, kterou použijete v uložených procedurách, se může lišit v závislosti na použitém poskytovateli.

Dále v mapě parametrů zadejte parametry, které jste použili v příkazu, a seznam parametrů v pořadí, v jakém byly provedeny v příkazu:

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param
END_PARAM_MAP()
```

Předchozí příklad definuje uloženou proceduru v průběhu jejího přechodu. Pro efektivní opakované použití kódu databáze obsahuje například sadu předdefinovaných uložených procedur s názvy, jako je `Sales by Year` nebo `dt_adduserobject`. Pomocí správce SQL Server Enterprise můžete zobrazit jejich definice. Můžete je zavolat následujícím způsobem (umístění *?* parametry závisejí na rozhraní uložené procedury):

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }"))
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }"))
```

Dále Deklarujte třídu příkazu:

```cpp
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>
```

Nakonec zavolejte uloženou proceduru v `OpenRowset` následujícím způsobem:

```cpp
CSession m_session;

HRESULT OpenRowset()
{
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);
}
```

Všimněte si také, že můžete definovat uloženou proceduru pomocí atributu databáze [db_command](../../windows/db-command.md) následujícím způsobem:

```cpp
db_command("{ ? = CALL dbo.dt_adduserobject }")
```

## <a name="see-also"></a>Viz také

[Použití uložených procedur](../../data/oledb/using-stored-procedures.md)
