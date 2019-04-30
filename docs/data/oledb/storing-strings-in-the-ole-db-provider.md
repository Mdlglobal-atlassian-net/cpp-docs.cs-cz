---
title: Ukládání řetězců ve zprostředkovateli OLE DB
ms.date: 10/26/2018
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: 5dce7dac84ef69da17baac135a68bd78698c4456
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344974"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Ukládání řetězců ve zprostředkovateli OLE DB

V *vlastní*RS.h, **Průvodce zprostředkovatelem ATL OLE DB** vytvoří výchozí uživatelský záznam nazvaný `CWindowsFile`. Chcete-li zpracovat dva řetězce, upravte `CWindowsFile` jak je znázorněno v následujícím kódu:

```cpp
////////////////////////////////////////////////////////////////////////
class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
DWORD dwBookmark;
static const int iSize = 256;    // Add this
TCHAR szCommand[iSize];          // Add this
TCHAR szText[iSize];             // Add this
TCHAR szCommand2[iSize];         // Add this
TCHAR szText2[iSize];            // Add this

BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)

   PROVIDER_COLUMN_ENTRY_STR("Command", 6, szCommand)    // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text", 7, szText)          // Add this
   PROVIDER_COLUMN_ENTRY_STR("Command2", 8, szCommand2)  // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text2", 9, szText2)        // Add this
END_PROVIDER_COLUMN_MAP()

   bool operator==(const CCustomWindowsFile& am) // This is optional
   {
      return (lstrcmpi(cFileName, am.cFileName) == 0);
   }
};
```

Datové členy `szCommand` a `szText` představují dva řetězce s `szCommand2` a `szText2` s další sloupce v případě potřeby. Datový člen `dwBookmark` pro tohoto jednoduchého zprostředkovatele pouze pro čtení není potřeba, ale se později používá k přidání `IRowsetLocate` rozhraní; viz [rozšíření jednoduchého číst pouze zprostředkovatele](../../data/oledb/enhancing-the-simple-read-only-provider.md). `==` Operátor porovná instancí (implementace tohoto operátoru je volitelný).

Když to uděláte, můžete přidat funkce [načtení řetězců do zprostředkovatele OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).

## <a name="see-also"></a>Viz také:

[Implementace jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
