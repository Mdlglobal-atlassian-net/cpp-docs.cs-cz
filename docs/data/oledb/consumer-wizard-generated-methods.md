---
title: Metody generované v Průvodci příjemcem | Microsoft Docs
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
ms.openlocfilehash: c0e03d24f61b3eba1ff4c6fa1e4d888a0252a21b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098599"
---
# <a name="consumer-wizard-generated-methods"></a>Metody generované v průvodci příjemcem
Průvodce příjemcem knihovny ATL technologie OLE DB a Průvodce aplikací MFC generovat určité funkce, kterých byste měli vědět. Všimněte si, že některé metody jsou implementované jinak v s atributy projekty, takže se několik aspektů; každý případ je popsané níže. Informace o zobrazení vloženého kódu najdete v tématu [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).  
  
-   `OpenAll` zdroj dat, sadu řádků, se otevře a spustí záložky, pokud jsou k dispozici.  
  
-   `CloseAll` Zavře všechny otevřené sady řádků a uvolní všechny spuštění příkazu.  
  
-   `OpenRowset` je volána OpenAll k otevření sady řádků příjemce nebo sady řádků.  
  
-   `GetRowsetProperties` načte ukazatel nastavit vlastnosti, které lze nastavit vlastností sady řádků.  
  
-   `OpenDataSource` Otevře se zdroji dat pomocí inicializačního řetězce, které jste zadali v **vlastnosti propojení dat** dialogové okno.  
  
-   `CloseDataSource` Zavře zdroj dat odpovídajícím způsobem.  
  
## <a name="openall-and-closeall"></a>OpenAll a CloseAll  
  
```  
HRESULT OpenAll();   

void CloseAll();  
```  
  
 Následující příklad ukazuje, jak můžete volat `OpenAll` a `CloseAll` při spuštění stejného příkazu opakovaně. Porovnání příklad kódu v [CCommand::Close](../../data/oledb/ccommand-close.md), který zobrazí variace, zavolá **Zavřít** a `ReleaseCommand` místo `CloseAll`.  
  
```  
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
 Všimněte si, že pokud definujete `HasBookmark` metody `OpenAll` kód nastaví vlastnost DBPROP_IRowsetLocate; zajistěte, aby toto provádíte pouze pokud váš poskytovatel podporuje dané vlastnosti.  
  
## <a name="openrowset"></a>OpenRowset  
  
```  
// OLE DB Template version:   
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);  
```  
  
 **OpenAll** volá tuto metodu za účelem otevření sady řádků nebo sady řádků v příjemci. Obvykle není potřeba volat `OpenRowset` Pokud chcete pracovat s více zdrojů dat nebo relací nebo sady řádků. `OpenRowset` je deklarován v souboru záhlaví třídy příkazu nebo tabulky:  
  
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
  
 Tuto metodu implementovat atributy jinak. Tato verze přebírá objekt relace a příkaz řetězec, který použije se výchozí hodnota příkaz řetězec zadaný v db_command, i když můžete předat jiný. Všimněte si, že pokud definujete `HasBookmark` metody `OpenRowset` kód nastaví vlastnost DBPROP_IRowsetLocate; zajistěte, aby toto provádíte pouze pokud váš poskytovatel podporuje dané vlastnosti.  
  
```  
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
  
## <a name="getrowsetproperties"></a>GetRowsetProperties –  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet);  
```  
  
 Tato metoda načte ukazatel na sadu vlastností sady řádků; Chcete-li nastavit vlastnosti, například DBPROP_IRowsetChange můžete použít tento ukazatel. `GetRowsetProperties` se používá v třídě uživatelského záznamu následujícím způsobem. Můžete upravit tento kód pro nastavení dalších vlastností sady řádků:  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
## <a name="remarks"></a>Poznámky  
 Neměli byste definovat globální konfiguraci `GetRowsetProperties` metoda vzhledem k tomu může dojít ke konfliktu s ten definované v průvodci. Upozorňujeme, že to je generované v Průvodci metodu, kterou dostanete s použitím šablon a s atributy projekty; Tento kód není vloží atributy.  
  
## <a name="opendatasource-and-closedatasource"></a>OpenDataSource a CloseDataSource  
  
```  
HRESULT OpenDataSource();   

void CloseDataSource();  
```  
  
## <a name="remarks"></a>Poznámky  
 Definuje metody, průvodce `OpenDataSource` a `CloseDataSource`; `OpenDataSource` volání [CDataSource::OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření příjemce OLE DB pomocí průvodce](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)