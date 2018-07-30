---
title: Metody generované v Průvodci příjemcem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OpenAll method
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- methods [C++], OLE DB Consumer Wizard-generated
- CloseDataSource method
- consumer wizard-generated classes and methods
- OpenDataSource method
- CloseAll method
- OpenRowset method
- GetRowsetProperties method
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9c8a3605a94e0feffa1072d1c7cd92a8bdfecb66
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340877"
---
# <a name="consumer-wizard-generated-methods"></a>Metody generované v průvodci příjemcem
Průvodce příjemcem ATL OLE DB a Průvodce aplikací MFC generovat určité funkce, které byste měli vědět. Všimněte si, že některé metody jsou implementovány odlišně v projektech s atributy, tedy několik upozornění; každý případ je popsané níže. Informace o zobrazení vloženého kódu najdete v tématu [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).  
  
-   `OpenAll` Otevře se zdroji dat sady řádků a zapne záložky, pokud jsou k dispozici.  
  
-   `CloseAll` Zavře všechny otevřené sady řádků a uvolní všech provedení příkazu.  
  
-   `OpenRowset` je volán OpenAll otevřete příjemce sady řádků nebo sady řádků.  
  
-   `GetRowsetProperties` načte ukazatel na nastavit pomocí vlastnosti, které můžete nastavit vlastnost sady řádků.  
  
-   `OpenDataSource` Otevře se zdroji dat pomocí inicializačního řetězce, které jste zadali v **vlastnosti propojení dat** dialogové okno.  
  
-   `CloseDataSource` zdroj dat se zavře vhodným způsobem.  
  
## <a name="openall-and-closeall"></a>OpenAll – a CloseAll  
  
```cpp  
HRESULT OpenAll();   

void CloseAll();  
```  
  
 Následující příklad ukazuje, jak můžete volat `OpenAll` a `CloseAll` při spuštění stejného příkazu opakovaně. Porovnání v příkladu kódu v [CCommand::Close](../../data/oledb/ccommand-close.md), který zobrazuje změnu, která volá `Close` a `ReleaseCommand` místo `CloseAll`.  
  
```cpp  
int main(int argc, char* argv[])  
{  
   HRESULT hr;  
  
   hr = CoInitialize(NULL);  
  
   CCustOrdersDetail rs;      // Your CCommand-derived class  
   rs.m_OrderID = 10248;      // Open order 10248  
   hr = rs.OpenAll();         // (Open also executes the command)  
   hr = rs.MoveFirst();         // Move to the first row and print it  
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );  
  
   // Close the first command execution  
   rs.Close();  
  
   rs.m_OrderID = 10249;      // Open order 10249 (a new order)  
   hr = rs.Open();            // (Open also executes the command)  
   hr = rs.MoveFirst();         // Move to the first row and print it  
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );  
  
   // Close the second command execution;  
   // Instead of rs.CloseAll() you could call  
   // rs.Close() and rs.ReleaseCommand():  
   rs.CloseAll();  
  
   CoUninitialize();  
   return 0;  
}  
```  
  
## <a name="remarks"></a>Poznámky  
 Všimněte si, že definujete `HasBookmark` metody `OpenAll` kódu nastaví vlastnost DBPROP_IRowsetLocate, ujistěte se, že pouze uděláte Pokud poskytovatel podporuje dané vlastnosti.  
  
## <a name="openrowset"></a>OpenRowset  
  
```cpp  
// OLE DB Template version:   
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);  
```  
  
 `OpenAll` volá tuto metodu za účelem otevření sady řádků nebo sady řádků v příjemci. Obvykle není potřeba volat `OpenRowset` Pokud budete chtít pracovat s více zdroji dat a relace a sady řádků. `OpenRowset` je deklarována v souboru hlaviček třídy příkazu nebo tabulky:  
  
```  
// OLE DB Template version:  
HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)  
{  
   HRESULT hr = Open(m_session, NULL, pPropSet);  
   #ifdef _DEBUG  
   if(FAILED(hr))  
      AtlTraceErrorRecords(hr);  
   #endif  
   return hr;  
}  
```  
  
 Tuto metodu implementovat atributy odlišně. Tato verze má objekt relace a příkaz řetězec, který se použije výchozí příkaz řetězec zadaný v db_command, i když lze předat jiné. Všimněte si, že definujete `HasBookmark` metody `OpenRowset` kódu nastaví vlastnost DBPROP_IRowsetLocate, ujistěte se, že pouze uděláte Pokud poskytovatel podporuje dané vlastnosti.  
  
```cpp  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand=NULL)  
{  
  
   DBPROPSET *pPropSet = NULL;  
   CDBPropSet propset(DBPROPSET_ROWSET);  
   __if_exists(HasBookmark)  
  
   {  
      propset.AddProperty(DBPROP_IRowsetLocate, true);  
      pPropSet= &propset;  
      }  
...  
}  
```  
  
## <a name="getrowsetproperties"></a>GetRowsetProperties  
  
```cpp 
void GetRowsetProperties(CDBPropSet* pPropSet);  
```  
  
 Tato metoda načte ukazatel na sadu vlastností v sadě řádků; Chcete-li nastavit vlastnosti, jako je DBPROP_IRowsetChange můžete použít tento ukazatel. `GetRowsetProperties` se používá ve třídě záznamů uživatele následujícím způsobem. Můžete upravit tento kód pro nastavení dalších vlastností sady řádků:  
  
```cpp  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
## <a name="remarks"></a>Poznámky  
 Neměli byste definovat globální `GetRowsetProperties` protože by mohla v konfliktu s tím definována metoda průvodcem. Všimněte si, že se jedná o metody generované v průvodci, který můžete začít s projekty bez vizuálního vzhledu a s atributy; atributy nejsou vložit tento kód.  
  
## <a name="opendatasource-and-closedatasource"></a>OpenDataSource a CloseDataSource  
  
```cpp  
HRESULT OpenDataSource();   

void CloseDataSource();  
```  
  
## <a name="remarks"></a>Poznámky  
 Průvodce definuje metody `OpenDataSource` a `CloseDataSource`; `OpenDataSource` volání [CDataSource::OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření příjemce OLE DB pomocí průvodce](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)