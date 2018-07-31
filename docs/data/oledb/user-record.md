---
title: Uživatelský záznam | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6b53410c8116f88d51734bb302026a03994e520a
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338191"
---
# <a name="user-record"></a>Uživatelský záznam
Záznam uživatele poskytuje strukturu kód a data, která představuje sloupci data pro sadu řádků. Uživatelský záznam lze vytvořit v době kompilace nebo za běhu. Při vytváření poskytovatele Průvodce zprostředkovatelem ATL OLE DB pomocí Průvodce vytvoří výchozí uživatelský záznam, který vypadá takto (za předpokladu, že zadaný název poskytovatele [krátký název] "MyProvider"):  
  
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
  
 Šablony zprostředkovatele OLE DB zpracovat všechny technologie OLE DB specifika týkající se interakce s klientem. Získat sloupce data potřebná pro odpověď, volá zprostředkovatele `GetColumnInfo` funkce, která je nutné umístit v záznamu uživatele. Můžete explicitně přepsat `GetColumnInfo` v záznamu uživatele, například podle jeho deklarací v souboru .h jak je znázorněno zde:  
  
```cpp  
template <class T>  
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)   
```  
  
 To je ekvivalentní:  
  
```cpp  
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)  
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)  
```  
  
 Musíte také implementovat `GetColumnInfo` v záznamu uživatele soubor .cpp.  
  
 Makra Provider Column Map pomáhají při vytváření `GetColumnInfo` funkce:  
  
-   BEGIN_PROVIDER_COLUMN_MAP definuje prototyp funkce a statická pole `ATLCOLUMNINFO` struktury.  
  
-   PROVIDER_COLUMN_ENTRY definuje a inicializuje jediného `ATLCOLUMNINFO`.  
  
-   END_PROVIDER_COLUMN_MAP zavře pole a funkce. Počet prvků pole do také umístí *pcCols* parametru.  
  
 Když se vytvoří záznam uživatele v době běhu `GetColumnInfo` používá *pThis* parametr přijímat ukazatel na instanci sady řádků nebo příkaz. Příkazy a sady řádků musí podporovat `IColumnsInfo` rozhraní, takže z tohoto ukazatele lze získat informace o sloupci.  
  
 `CommandClass` a `RowsetClass` příkazu a sady řádků, které používají uživatelský záznam.  
  
 Podrobnější příklad toho, jak přepsat `GetColumnInfo` v záznamu uživatele, najdete v článku [dynamické určování sloupců vrácených příjemci](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Viz také  
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)