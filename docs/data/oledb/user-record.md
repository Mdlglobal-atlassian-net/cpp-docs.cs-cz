---
title: Uživatelský záznam
ms.date: 05/09/2019
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
ms.openlocfilehash: d6920a73f107f226cc31cb27fd15178f6d2f1c26
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525256"
---
# <a name="user-record"></a>Uživatelský záznam

> [!NOTE] 
> Průvodce zprostředkovatele ATL OLE DB není k dispozici v aplikaci Visual Studio 2019 a novějším.

Záznam uživatele poskytuje strukturu kód a data, která představuje sloupci data pro sadu řádků. Uživatelský záznam lze vytvořit v době kompilace nebo za běhu. Když vytvoříte poskytovatele prostřednictvím **Průvodce zprostředkovatelem ATL OLE DB**, Průvodce vytvoří výchozí uživatelský záznam, který vypadá takto (za předpokladu, že zadaný název zprostředkovatele [krátký název] z *MyProvider*):

```cpp
class CWindowsFile:
   public WIN32_FIND_DATA
{
public:
  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
  
};
```

Šablony zprostředkovatele OLE DB zpracovat všechny specifikace technologie OLE DB na interakce s klientem. Získat sloupce data potřebná pro odpověď, volá zprostředkovatele `GetColumnInfo` funkce, která je nutné umístit v záznamu uživatele. Můžete explicitně přepsat `GetColumnInfo` v záznamu uživatele, například podle jeho deklarací v souboru .h jak je znázorněno zde:

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols) 
```

To odpovídá:

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

Poté, implementujte `GetColumnInfo` v záznamu uživatele soubor .cpp.

Makra Provider Column Map pomáhají při vytváření `GetColumnInfo` funkce:

- BEGIN_PROVIDER_COLUMN_MAP definuje prototyp funkce a statická pole `ATLCOLUMNINFO` struktury.

- PROVIDER_COLUMN_ENTRY definuje a inicializuje jediného `ATLCOLUMNINFO`.

- END_PROVIDER_COLUMN_MAP zavře pole a funkce. Počet prvků pole do také umístí *pcCols* parametru.

Když se vytvoří záznam uživatele v době běhu `GetColumnInfo` používá *pThis* parametr přijímat ukazatel na instanci sady řádků nebo příkaz. Příkazy a sady řádků musí podporovat `IColumnsInfo` tak informace o sloupci můžete provést z tohoto ukazatele rozhraní.

`CommandClass` a `RowsetClass` příkazu a sady řádků, které používají uživatelský záznam.

Podrobnější příklad toho, jak přepsat `GetColumnInfo` v záznamu uživatele, najdete v článku [dynamické určování sloupců vrácených příjemci](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Viz také:

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
