---
title: Ukládání řetězců ve zprostředkovateli OLE DB
ms.date: 10/26/2018
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: b1bc7ca74ce114f9d901fc5771a376df973f54a8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652332"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Ukládání řetězců ve zprostředkovateli OLE DB

V souboru MyProviderRS.h **Průvodce zprostředkovatelem ATL OLE DB** vytvoří výchozí uživatelský záznam nazvaný `CWindowsFile`. Chcete-li zpracovat dva řetězce, buď upravte `CWindowsFile` nebo přidejte záznam uživatele, jak je znázorněno v následujícím kódu:

```cpp
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

Datové členy `szCommand` a `szText` představují dva řetězce s `szCommand2` a `szText2` s další sloupce v případě potřeby. Datový člen `dwBookmark` pro tohoto jednoduchého zprostředkovatele pouze pro čtení není potřeba, ale se později používá k přidání `IRowsetLocate` rozhraní; viz [rozšíření jednoduchého číst pouze zprostředkovatele](../../data/oledb/enhancing-the-simple-read-only-provider.md). `==` Operátor porovná instancí (implementace tohoto operátoru je volitelný).

Když to uděláte, váš poskytovatel by měl být připraveni zkompilovat a spustit. Testování zprostředkovatele, budete potřebovat příjemce s odpovídající funkce. [Implementace jednoduchého příjemce](../../data/oledb/implementing-a-simple-consumer.md) ukazuje, jak vytvořit testovací příjemce. Spusťte test příjemce s tímto poskytovatelem. Ověřte, že příjemce testů obdrží správné řetězce od poskytovatele po kliknutí **spustit** tlačítko **zkušební příjemce** dialogové okno.

Pokud jste úspěšně otestovat poskytovatele, může být vhodné k vylepšení svých funkcí implementací další rozhraní. Příklad je uveden v [rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md).

## <a name="see-also"></a>Viz také

[Implementace jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
