---
title: Ukládání řetězců ve zprostředkovateli OLE DB
ms.date: 05/09/2019
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: 1d6d2b73495d5ca6e275b13ed3c430f8169179d4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079113"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Ukládání řetězců ve zprostředkovateli OLE DB

> [!NOTE]
> Průvodce zprostředkovatelem OLE DB ATL není k dispozici v aplikaci Visual Studio 2019 a novější.

V *vlastní*RS. h vytvoří **Průvodce OLE DB zprostředkovatele ATL** výchozí záznam uživatele s názvem `CWindowsFile`. Chcete-li zpracovat dva řetězce, upravte `CWindowsFile`, jak je znázorněno v následujícím kódu:

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

Datové členy `szCommand` a `szText` reprezentují dva řetězce a v případě potřeby `szCommand2` a `szText2` s dalšími sloupci. Datový člen `dwBookmark` není potřebný pro tohoto jednoduchého zprostředkovatele pouze pro čtení, ale používá se později k přidání rozhraní `IRowsetLocate`; Viz téma [rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md). Operátor `==` porovnává instance (implementace tohoto operátoru je nepovinná).

Až to uděláte, můžete [do poskytovatele OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md)přidat funkce pro čtení řetězců.

## <a name="see-also"></a>Viz také

[Implementace jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
