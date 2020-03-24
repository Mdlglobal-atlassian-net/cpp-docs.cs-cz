---
title: Metody generované v průvodci příjemcem
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, wizard-generated classes and methods
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
ms.openlocfilehash: ce2442909fd318187a1508300a75ff4f634b3410
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211507"
---
# <a name="consumer-wizard-generated-methods"></a>Metody generované v průvodci příjemcem

::: moniker range="vs-2019"

Průvodce příjemcem OLE DB ATL není v aplikaci Visual Studio 2019 a novějších k dispozici. Tuto funkci můžete přesto přidat ručně.

::: moniker-end

::: moniker range="<=vs-2017"

**Průvodce OLE DB příjemce ATL** a **Průvodce aplikací MFC** vygeneruje některé funkce, o kterých byste měli vědět. Některé metody jsou v projektech s atributy implementovány jinak, takže existuje několik aspektů. jednotlivé případy jsou uvedeny níže. Informace o zobrazení vloženého kódu naleznete v tématu [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).

- `OpenAll` otevře zdroj dat, sady řádků a zapne záložky, pokud jsou k dispozici.

- `CloseAll` zavře všechny otevřené sady řádků a uvolní všechny provádění příkazů.

- `OpenRowset` je volána `OpenAll` k otevření sady řádků nebo sad řádků daného uživatele.

- `GetRowsetProperties` načte ukazatel na sadu vlastností sady řádků, pomocí které lze nastavit vlastnosti.

- `OpenDataSource` otevře zdroj dat pomocí inicializačního řetězce, který jste zadali v dialogovém okně **vlastnosti propojení dat** .

- `CloseDataSource` zavírá zdroj dat vhodným způsobem.

## <a name="openall-and-closeall"></a>OpenAll a CloseAll

```cpp
HRESULT OpenAll();

void CloseAll();
```

Následující příklad ukazuje, jak lze volat `OpenAll` a `CloseAll` při opakovaném spuštění stejného příkazu. Porovnejte příklad kódu v [CCommand:: Close](../../data/oledb/ccommand-close.md), který zobrazuje variaci, která volá `Close` a `ReleaseCommand` namísto `CloseAll`.

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

### <a name="remarks"></a>Poznámky

Definujete-li metodu `HasBookmark`, kód `OpenAll` nastaví vlastnost `DBPROP_IRowsetLocate`; Ujistěte se, že to uděláte jenom v případě, že poskytovatel tuto vlastnost podporuje.

## <a name="openrowset"></a>OpenRowset

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);
```

`OpenAll` volá tuto metodu, aby otevřela sadu řádků nebo sady řádků ve spotřebiteli. Obvykle nemusíte volat `OpenRowset`, pokud nechcete pracovat s více zdroji dat/relacemi a sadami řádků. `OpenRowset` je deklarován v souboru hlaviček třídy příkazu nebo tabulky:

```cpp
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

Atributy implementují tuto metodu odlišně. Tato verze přebírá objekt Session a řetězec příkazu, který je výchozím nastavením řetězce příkazu zadaného v db_command, i když můžete předat jiný. Definujete-li metodu `HasBookmark`, kód `OpenRowset` nastaví vlastnost `DBPROP_IRowsetLocate`; Ujistěte se, že to uděláte jenom v případě, že poskytovatel tuto vlastnost podporuje.

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

Tato metoda načte ukazatel na sadu vlastností sady řádků. Tento ukazatel lze použít k nastavení vlastností, například `DBPROP_IRowsetChange`. `GetRowsetProperties` se ve třídě záznamu uživatele používá následujícím způsobem. Úpravou tohoto kódu můžete nastavit další vlastnosti sady řádků:

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="remarks"></a>Poznámky

Nedefinujte globální `GetRowsetProperties` metodu, protože by mohla být v konfliktu s rozhraním definovaným průvodcem. Toto je metoda vygenerovaná průvodcem, kterou získáte s použitím šablon a projektů s atributy. atributy nevkládají tento kód.

## <a name="opendatasource-and-closedatasource"></a>OpenDataSource a CloseDataSource

```cpp
HRESULT OpenDataSource();

void CloseDataSource();
```

### <a name="remarks"></a>Poznámky

Průvodce definuje metody `OpenDataSource` a `CloseDataSource`; `OpenDataSource` volá [CDataSource:: OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md).

::: moniker-end

## <a name="see-also"></a>Viz také

[Vytvoření příjemce OLE DB pomocí průvodce](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
