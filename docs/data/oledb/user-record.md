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
ms.openlocfilehash: 4a8fb6c9eeee3736501a04a095bdd763de16de7d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079006"
---
# <a name="user-record"></a>Uživatelský záznam

> [!NOTE]
> Průvodce zprostředkovatelem OLE DB ATL není k dispozici v aplikaci Visual Studio 2019 a novější.

Záznam uživatele poskytuje strukturu kódu a dat, která představuje data sloupce pro sadu řádků. Záznam uživatele lze vytvořit v době kompilace nebo v době běhu. Když vytvoříte poskytovatele pomocí **průvodce OLE DB zprostředkovatele ATL**, vytvoří průvodce výchozí záznam uživatele, který bude vypadat nějak takto (za předpokladu, že jste zadali název zprostředkovatele [krátký název] *MyProvider*):

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

Šablony poskytovatele OLE DB zpracovávají všechny OLE DB specifické pro interakce s klientem. Aby bylo možné získat data sloupce potřebná pro odpověď, zprostředkovatel zavolá funkci `GetColumnInfo`, kterou je nutné umístit do záznamu uživatele. Můžete explicitně přepsat `GetColumnInfo` v záznamu uživatele, například jeho deklarováním v souboru. h, jak je znázorněno zde:

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)
```

To je rovno:

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

Potom implementujte `GetColumnInfo` v souboru. cpp záznamu uživatele.

PROVIDER_COLUMN_MAP makra pomáhají při vytváření funkce `GetColumnInfo`:

- BEGIN_PROVIDER_COLUMN_MAP definuje prototyp funkce a statické pole `ATLCOLUMNINFO` struktur.

- PROVIDER_COLUMN_ENTRY definuje a inicializuje jeden `ATLCOLUMNINFO`.

- END_PROVIDER_COLUMN_MAP zavře pole a funkci. Také umístí prvky pole do parametru *pcCols* .

Při vytvoření záznamu uživatele v době běhu `GetColumnInfo` používá parametr *pThis* k přijetí ukazatele na instanci sady řádků nebo příkazu. Příkazy a sady řádků musí podporovat rozhraní `IColumnsInfo`, takže informace o sloupci je možné z tohoto ukazatele považovat.

`CommandClass` a `RowsetClass` jsou příkazy a sady řádků, které používají záznam uživatele.

Podrobnější příklad, jak přepsat `GetColumnInfo` v záznamu uživatele, najdete v tématu [Dynamické určování sloupců vrácených příjemci](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Viz také

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
