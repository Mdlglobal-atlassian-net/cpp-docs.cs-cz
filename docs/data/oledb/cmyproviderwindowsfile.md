---
title: CMyProviderWindowsFile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cmyproviderwindowsfile
dev_langs: C++
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 63143532c5f5ad770c6234a24fbedf1b478ba143
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmyproviderwindowsfile"></a>CMyProviderWindowsFile
Průvodce vytvoří třídu obsahující jeden řádek dat; v takovém případě se nazývá `CMyProviderWindowsFile`. Následující kód pro `CMyProviderWindowsFile` je generován průvodcem a uvádí všechny soubory v adresáři pomocí **WIN32_FIND_DATA** struktura. `CMyProviderWindowsFile`dědí z **WIN32_FIND_DATA** strukturu:  
  
```  
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
  
 `CMyProviderWindowsFile`je volána [třída uživatelského záznamu](../../data/oledb/user-record.md) protože také obsahuje mapu popisující sloupce v sadě řádků zprostředkovatele. Mapování sloupce zprostředkovatele obsahuje jeden záznam pro každé pole v sadě řádků pomocí makra PROVIDER_COLUMN_ENTRY. Makra zadejte název sloupce, pořadové číslo a posunutí k položce struktury. Položky sloupce zprostředkovatele ve výše uvedeném kódu obsahují posun do **WIN32_FIND_DATA** struktura. Když příjemce volá **IRowset::GetData**, data se přenáší v jedné souvislé vyrovnávací paměti. Namísto provádění aritmetika ukazatele, mapy umožňuje zadat datový člen.  
  
 `CMyProviderRowset` Třída také obsahuje `Execute` metoda. `Execute`je ve skutečnosti co čte data z nativní zdroje. Následující kód ukazuje vygenerované průvodcem `Execute` metoda. Funkce, která používá Win32 **FindFirstFile** a `FindNextFile` rozhraní API pro načtení informací o souborech v adresáři a umístit je instance `CMyProviderWindowsFile` třídy.  
  
```  
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
  
 Adresář, který chcete vyhledat je reprezentována `m_strCommandText`; obsahuje text reprezentován `ICommandText` rozhraní v objektu command. Pokud není zadán žádný adresář, používá aktuální adresář.  
  
 Metoda vytvoří jeden záznam pro každý soubor (odpovídající řádek) a umístí jej do **m_rgRowData** – datový člen. `CRowsetImpl` Třída definuje **m_rgRowData** – datový člen. Data v toto pole představuje celou tabulku a bude použit v rámci šablony.  
  
## <a name="see-also"></a>Viz také  
 [Poskytovatel souborů vytvořených průvodcem](../../data/oledb/provider-wizard-generated-files.md)