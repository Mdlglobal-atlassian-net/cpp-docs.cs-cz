---
title: CCustomWindowsFile
ms.date: 10/22/2018
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
ms.openlocfilehash: 103a1ce5568c6137994056e574ce8eec04511d8f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079746"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

Průvodce vytvoří třídu, která má jeden řádek dat; v tomto případě se nazývá `CCustomWindowsFile`. Následující kód pro `CCustomWindowsFile` je vygenerován průvodcem a zobrazí seznam všech souborů v adresáři pomocí struktury `WIN32_FIND_DATA`. `CCustomWindowsFile` dědí ze struktury `WIN32_FIND_DATA`:

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
};
```

`CCustomWindowsFile` se nazývá [Třída záznamu uživatele](../../data/oledb/user-record.md) , protože má také mapu popisující sloupce v sadě řádků poskytovatele. Mapa sloupce Provider obsahuje jednu položku pro každé pole v sadě řádků pomocí PROVIDER_COLUMN_ENTRY maker. Makra určují název sloupce, ordinální číslo a posun na položku struktury. Položky sloupce poskytovatele ve výše uvedeném kódu obsahují posuny do `WIN32_FIND_DATA` struktury. Když příjemce volá `IRowset::GetData`, data se přenesou do jedné souvislé vyrovnávací paměti. Místo toho, abyste mohli provádět aritmetické operace s ukazatelem, vám mapa umožní zadat datový člen.

Třída `CCustomRowset` obsahuje také metodu `Execute`. `Execute` je to, co skutečně čte data z nativního zdroje. Následující kód ukazuje `Execute` metodu generovanou průvodcem. Funkce používá rozhraní Win32 `FindFirstFile` a rozhraní API `FindNextFile` k načtení informací o souborech v adresáři a jejich umístění do instancí třídy `CCustomWindowsFile`.

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
{
   USES_CONVERSION;
   BOOL bFound = FALSE;
   HANDLE hFile;
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :
       OLE2T(m_strCommandText);
   CCustomWindowsFile wf;
   hFile = FindFirstFile(szDir, &wf);
   if (hFile == INVALID_HANDLE_VALUE)
      return DB_E_ERRORSINCOMMAND;
   LONG cFiles = 1;
   BOOL bMoreFiles = TRUE;
   while (bMoreFiles)
   {
      if (!m_rgRowData.Add(wf))
         return E_OUTOFMEMORY;
      bMoreFiles = FindNextFile(hFile, &wf);
      cFiles++;
   }
   FindClose(hFile);
   if (pcRowsAffected != NULL)
      *pcRowsAffected = cFiles;
   return S_OK;
}
```

Adresář pro hledání je zobrazen pomocí `m_strCommandText`; obsahuje text reprezentovaný rozhraním `ICommandText` v objektu Command. Pokud není zadán žádný adresář, použije se aktuální adresář.

Metoda vytvoří jednu položku pro každý soubor (odpovídající řádku) a umístí jej do datového členu `m_rgRowData`. Třída `CRowsetImpl` definuje datový člen `m_rgRowData`. Data v tomto poli se zobrazí v celé tabulce a používají se v celém šablonách.

## <a name="see-also"></a>Viz také

[Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)<br/>
