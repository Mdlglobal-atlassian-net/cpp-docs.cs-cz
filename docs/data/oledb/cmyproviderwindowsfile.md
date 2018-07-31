---
title: CMyProviderWindowsFile | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderwindowsfile
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0f18f5a524cbfbfa7f17dfd3964c68329bc8a042
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338503"
---
# <a name="cmyproviderwindowsfile"></a>CMyProviderWindowsFile
Průvodce vytvoří třídu pro obsahovat jeden řádek dat; v takovém případě se nazývá `CMyProviderWindowsFile`. Následující kód pro `CMyProviderWindowsFile` je vygenerovaný průvodcem a uvádí všechny soubory v adresáři s použitím `WIN32_FIND_DATA` struktury. `CMyProviderWindowsFile` dědí z `WIN32_FIND_DATA` struktury:  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
class CMyProviderWindowsFile:   
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
  
 `CMyProviderWindowsFile` je volána [třídy uživatelského záznamu](../../data/oledb/user-record.md) protože také obsahuje mapování popisující sloupce v sadě řádků %{Rowset/ poskytovatele. Mapování sloupce poskytovatele obsahuje jeden záznam pro každé pole v sadě řádků %{Rowset/ použití maker PROVIDER_COLUMN_ENTRY. Makra zadejte název sloupce, pořadí a posun k položce struktury. Sloupec položky zprostředkovatele ve výše uvedeném kódu obsahují posun do `WIN32_FIND_DATA` struktury. Když příjemce volá `IRowset::GetData`, data se přenáší do jedné souvislé vyrovnávací paměti. Místo toho můžete provést aritmetiku ukazatele, mapy můžete zadat datový člen.  
  
 `CMyProviderRowset` Třída také obsahuje `Execute` metody. `Execute` je, co skutečně čte data z nativní zdroje. Následující kód ukazuje generované průvodcem `Execute` metody. Využívá rozhraní Win32 funkce `FindFirstFile` a `FindNextFile` rozhraní API k načtení informací o souborech v adresáři a umístit je do instance `CMyProviderWindowsFile` třídy.  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)  
{  
   USES_CONVERSION;  
   BOOL bFound = FALSE;  
   HANDLE hFile;  
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :  
       OLE2T(m_strCommandText);  
   CMyProviderWindowsFile wf;  
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
  
 Adresář hledání je reprezentován `m_strCommandText`; obsahuje text reprezentován `ICommandText` rozhraní příkazového objektu. Pokud není zadán žádný adresář, použije aktuální adresář.  
  
 Metoda vytvoří jeden záznam pro každý soubor (odpovídající řádek) a umístí jej do `m_rgRowData` datový člen. `CRowsetImpl` Třída definuje `m_rgRowData` datový člen. Data v tomto poli představuje celou tabulku a používá se v rámci šablony.  
  
## <a name="see-also"></a>Viz také  
 [Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)