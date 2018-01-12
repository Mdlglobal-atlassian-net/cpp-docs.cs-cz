---
title: "Ukládání řetězců ve zprostředkovateli OLE DB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 11c058bacee52eb2b1df771a27d8695113f1c71d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Ukládání řetězců ve zprostředkovateli OLE DB
V souboru MyProviderRS.h, Průvodce zprostředkovatele OLE DB ATL vytvoří výchozí uživatelský záznam nazvaný `CWindowsFile`. Chcete-li zpracovat dva řetězce, buď změňte `CWindowsFile` nebo přidat vlastní záznam uživatele, jak je znázorněno v následujícím kódu:  
  
```  
////////////////////////////////////////////////////////////////////////  
class CAgentMan:   
   public WIN32_FIND_DATA  
   DWORD dwBookmark;              // Add this  
   TCHAR szCommand[256];          // Add this  
   TCHAR szText[256];             // Add this  
   TCHAR szCommand2[256];         // Add this  
   TCHAR szText2[256];            // Add this  
  
{  
public:  
BEGIN_PROVIDER_COLUMN_MAP()  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command"), 1, 256, GUID_NULL, CAgentMan, szCommand)  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text"), 2, 256, GUID_NULL, CAgentMan, szText)   
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command2"), 3, 256, GUID_NULL, CAgentMan, szCommand2)  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text2"),4, 256, GUID_NULL, CAgentMan, szText2)  
END_PROVIDER_COLUMN_MAP()  
   bool operator==(const CAgentMan& am) // This is optional   
   {  
      return (lstrcmpi(cFileName, wf.cFileName) == 0);  
   }  
};  
```  
  
 Datové členy `szCommand` a `szText` představují dva řetězce s `szCommand2` a `szText2` poskytují další sloupce v případě potřeby. Datový člen `dwBookmark` není vyžadován pro tohoto jednoduchého zprostředkovatele pouze pro čtení, ale se později používá k přidání `IRowsetLocate` rozhraní; viz [rozšíření jednoduchého číst pouze zprostředkovatele](../../data/oledb/enhancing-the-simple-read-only-provider.md). `==` Operátor porovná instancí (implementace tento operátor. je volitelný).  
  
 Když to uděláte, měli být připravení zkompilování a spuštění svého poskytovatele. Chcete-li otestovat zprostředkovatele, musíte příjemce s odpovídající funkce. [Implementace jednoduchého příjemce](../../data/oledb/implementing-a-simple-consumer.md) ukazuje, jak vytvořit testovací příjemce. Spusťte test příjemce s poskytovatelem. Ověřte, že zkušební příjemce obdrží správné řetězce od poskytovatele, po kliknutí **spustit** tlačítka na **zkušební příjemce** dialogové okno.  
  
 Pokud váš poskytovatel úspěšně testování, můžete zvýšit jeho funkce implementací další rozhraní. Příklad je uveden v [rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
## <a name="see-also"></a>Viz také  
 [Implementace jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md)