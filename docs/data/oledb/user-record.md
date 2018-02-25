---
title: "Uživatelský záznam | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cbb073aceaff855de700eae6d8aede148f9b8bcc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="user-record"></a>Uživatelský záznam
Záznamu uživatele obsahuje strukturu kód a data, která představuje data ve sloupci pro sadu řádků. Uživatelský záznam lze vytvořit v době kompilace nebo za běhu. Při vytváření zprostředkovatele pomocí Průvodce zprostředkovatele OLE DB ATL průvodce vytvoří výchozí záznam uživatele, který bude vypadat takto (za předpokladu, že jste zadali název zprostředkovatele [krátký název] "MyProvider"):  
  
```  
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
  
 Šablony zprostředkovatele technologie OLE DB zpracovávat všechny specifikace technologie OLE DB týkající se interakce s klientem. Získat data ve sloupci potřebných pro odpověď volá zprostředkovatele `GetColumnInfo` funkce, kterou je nutné umístit v záznamu uživatele. Můžete explicitně přepsat `GetColumnInfo` v záznamu uživatele, například pomocí deklarování v souboru h jak je vidět tady:  
  
```  
template <class T>  
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)   
```  
  
 Jde o ekvivalent:  
  
```  
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)  
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)  
```  
  
 Musíte také implementovat `GetColumnInfo` v souboru záznamu uživatele.  
  
 Makra Provider Column Map pomáhají při vytváření `GetColumnInfo` funkce:  
  
-   BEGIN_PROVIDER_COLUMN_MAP definují prototyp funkce a statické pole **ATLCOLUMNINFO** struktury.  
  
-   PROVIDER_COLUMN_ENTRY definuje a inicializuje jedné **ATLCOLUMNINFO**.  
  
-   END_PROVIDER_COLUMN_MAP zavře tohoto pole a funkce. Také zobrazuje pole elementu počítání do `pcCols` parametr.  
  
 Když se vytvoří záznam uživatele v době běhu **GetColumnInfo –** používá `pThis` parametr přijímat ukazatel na instanci sady řádků nebo příkaz. Musí podporovat příkazy a sady řádků `IColumnsInfo` rozhraní, tak ze tento ukazatel nelze získat informace o sloupci.  
  
 **CommandClass** a **RowsetClass** jsou příkazu a sady řádků, který pomocí záznamu uživatele.  
  
 Podrobnější příklad, jak lze přepsat `GetColumnInfo` v záznamu uživatele najdete v části [dynamické určování sloupců vrácených příjemci](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Viz také  
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)