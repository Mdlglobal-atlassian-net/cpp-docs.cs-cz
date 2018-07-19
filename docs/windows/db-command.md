---
title: db_command | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/10/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_command
dev_langs:
- C++
helpviewer_keywords:
- db_command attribute
ms.assetid: 714c3e15-85d7-408b-9a7c-88505c3e5d24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70399b15081de89d8da49268c8d62d3ad390858d
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "38954978"
---
# <a name="dbcommand"></a>db_command
Vytvoří příkaz OLE DB.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
[ db_command(   
   command,   
   name,   
   source_name,   
   hresult,   
   bindings,   
   bulk_fetch)  
]  
```  
  
### <a name="parameters"></a>Parametry  

*Příkaz*  
Příkaz řetězec obsahující text příkazu technologie OLE DB. Je jednoduchý příklad:  
  
```cpp
[ db_command ( command = "Select * from Products" ) ]  
```  
  
*Příkaz* syntaxe vypadá takto:  
    
> Vazba parametru bloku 1  
> &nbsp;&nbsp;Příkaz OLE DB  
> Vazba parametru bloku 2  
> &nbsp;&nbsp;pokračování příkaz OLE DB  
> Vazba parametru bloku 3  
> ...  
  
A *bloku vazby parametrů* je definovaná následujícím způsobem:  
  
> **(\[**  *bindtype* **]** *szVar1* \[, *szVar2* \[, *nVar3* \[;...]]] **)**  
  
 kde:  
  
- **(** označuje začátek příslušného datového bloku vazby.  
  
- **\[** *bindtype* **]** je jedním z následujících řetězců velká a malá písmena:  
  
  -   **\[db_column]** všechny proměnné členů váže ke sloupci v sadě řádků.  
  
  -   **\[bindto]** (stejné jako  **\[db_column]**).  
  
  -   **\[v]** váže členské proměnné jako vstupní parametry.  
  
  -   **\[out]** váže členské proměnné jako výstupní parametry.  
  
  -   **\[in, out]** váže členské proměnné jako vstupní a výstupní parametry.  
  
- *szVarX*, *nVarX* přeložit na proměnnou člena v aktuálním oboru.  
  
- **)** označuje konec datového bloku vazby.  
  
Pokud řetězec příkazu obsahuje jeden nebo více specifikátory jako \[v], \[out], nebo \[vstup a výstup], **db_command** vytvoří mapu parametr.  
  
Pokud řetězec příkazu obsahuje jeden nebo více parametrů jako \[db_column] nebo \[bindto], **db_command** generuje sadu řádků a mapování přístupový objekt pro tyto vazby proměnné. Zobrazit [db_accessor](../windows/db-accessor.md) Další informace.  
  
> [!NOTE]
> \[*bindtype*] syntaxe a *vazby* parametru jsou neplatné, při použití **db_command** na úrovni třídy.  
  
 Tady je několik příkladů vazby parametru bloky. Následující příklad vytvoří vazbu `m_au_fname` a `m_au_lname` datové členy `au_fname` a `au_lname` sloupce, z tabulky Autoři databáze pubs:  
  
```cpp  
TCHAR m_au_fname[21];  
TCHAR m_au_lname[41];  
TCHAR m_state[3] = 'CA';  
  
[db_command (  
   command = "SELECT au_fname([bindto]m_au_fname), au_lname([bindto]m_au_lname) " \  
   "FROM dbo.authors " \  
   "WHERE state = ?([in]m_state)")  
]
```
  
*Název* (volitelné)  
Název popisovače, který můžete použít pro práci se v sadě řádků. Pokud zadáte *název*, **db_command** vygeneruje třídu se zadaným *název*, které lze použít k procházení řádků nebo chcete-li spustit více dotazů akce. Pokud nezadáte *název*, nebude možné vrátit více než jeden řádek výsledků pro uživatele.  
  
*source_name* (volitelné)  
`CSession` Proměnnou nebo instance třídy, která má `db_source` atribut WebMethod na kterém příkaz spustí. Zobrazit [db_source](../windows/db-source.md).  
  
**db_command** kontroluje, ujistěte se, že proměnné použité pro *source_name* je platný, funkce nebo globální rozsah by tak měly být zadané proměnné.  
  
*HRESULT* (volitelné)  
Určuje proměnné, která se zobrazí `HRESULT` tohoto databázového příkazu. Pokud proměnná neexistuje, ji budou automaticky vloženy atribut.  
  
*vazby* (volitelné)  
Umožňuje oddělit vazby parametrů příkazu technologie OLE DB.  
  
Pokud zadáte hodnotu pro *vazby*, **db_command** provede analýzu přidruženou hodnotu a nebude analyzovat \[ *bindtype*] parametru. Toto použití můžete použít syntaxi zprostředkovatele OLE DB. Chcete-li zakázat analýzy bez vazby parametrů, zadejte **vazby = ""**.  
  
Pokud nezadáte hodnotu *vazby*, **db_command** provede analýzu bloku parametrů vazby, hledá "**(**" následovaný **\[** _bindtype_**]** v závorkách, za nímž následuje jedna nebo více dříve deklarovaný člen proměnné C++, za nímž následuje "**)**". Veškerý text v závorkách se odstraní z výsledné příkazu a tyto parametry se použije k vytvoření sloupce a parametr vazby tohoto příkazu.  
  
*bulk_fetch* (volitelné)  
Celočíselná hodnota, která určuje počet řádků, které mají načíst.  
  
Výchozí hodnota je 1, která určuje načítání jednoho řádku (řádků budou typu [CRowset](../data/oledb/crowset-class.md)).  
  
Hodnota, která je větší než 1 představuje hromadné načítání řádků. Hromadné načítání řádků s možností hromadné sady řádků k načtení více popisovačů řádků odkazuje (v sadě řádků budou typu [CBulkRowset](../data/oledb/cbulkrowset-class.md) a bude volat `SetRows` s zadaný počet řádků).  
  
Pokud *bulk_fetch* je menší než 1, `SetRows` vrátí nulu.  
  
## <a name="remarks"></a>Poznámky  
**db_command** vytvoří [CCommand](../data/oledb/ccommand-class.md) objekt, který používá příjemce technologie OLE DB ke spuštění příkazu.  
  
Můžete použít **db_command** s rozsahem třídy nebo funkce; Hlavní rozdíl je v oboru `CCommand` objektu. V oboru funkce data, jako jsou třeba vazby ukončit na konci funkce. Použití oboru třídy a funkce zahrnují třídy šablona příjemce technologie OLE DB **CCommand\<>**, ale liší se argumenty šablony pro případy funkce a třídy. V případě funkce bude proveden vazby **přistupující objekt** , která zahrnuje místní proměnné při použití třídy odvodí `CAccessor`-odvozené třídy jako argument. Když se použije jako atribut třídy **db_command** funguje ve spojení s **db_column**.  
  
**db_command** lze použít ke spuštění příkazů, které nevrací sadu výsledků dotazu.  
  
 Když příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor bude přejmenujte třídu na \_ *YourClassName*přístupový objekt, kde *YourClassName* je název, který jste zadali třídy a kompilátor vytvoří také třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd zobrazí se obě třídy.  
  
## <a name="example"></a>Příklad  
 Tato ukázka definuje příkaz, který vybere jména a příjmení z tabulky, jejichž sloupce pro stát odpovídá "CA". **db_command** vytvoří a načte sadu řádků, na kterém bude možné volat generované v Průvodci funkce, jako [OpenAll a CloseAll](../data/oledb/consumer-wizard-generated-methods.md), stejně jako `CRowset` členské funkce, jako například [MoveNext](../data/oledb/crowset-movenext.md).  
  
 Upozorňujeme, že tento kód vyžaduje, abyste zadali vlastní připojovací řetězec, který se připojuje k databázi pubs. Informace o tom, jak to udělat ve vývojovém prostředí najdete v tématu [postupy: připojení k databázi a procházejí existujících objektů](/sql/ssdt/how-to-connect-to-a-database-and-browse-existing-objects) a [přidat nové připojení](/visualstudio/data-tools/add-new-connections).  
  
```cpp  
// db_command.h  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
#pragma once  
  
[  db_source(L"your connection string"),  
   db_command(L" \  
      SELECT au_lname, au_fname \  
      FROM dbo.authors \  
      WHERE state = 'CA'")  ]  
  
struct CAuthors {  
   // In order to fix several issues with some providers, the code below may bind  
   // columns in a different order than reported by the provider  
  
   DBSTATUS m_dwau_lnameStatus;  
   DBSTATUS m_dwau_fnameStatus;  
   DBLENGTH m_dwau_lnameLength;  
   DBLENGTH m_dwau_fnameLength;  
  
   [ db_column("au_lname", status="m_dwau_lnameStatus", length="m_dwau_lnameLength") ] TCHAR m_au_lname[41];  
   [ db_column("au_fname", status="m_dwau_fnameStatus", length="m_dwau_fnameLength") ] TCHAR m_au_fname[21];  
  
   [ db_param("7", paramtype="DBPARAMIO_INPUT") ] TCHAR m_state[3];  
  
   void GetRowsetProperties(CDBPropSet* pPropSet) {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   }  
};  
```  
  
## <a name="example"></a>Příklad  
  
```cpp  
// db_command.cpp  
// compile with: /c  
#include "db_command.h"  
  
int main(int argc, _TCHAR* argv[]) {  
   HRESULT hr = CoInitialize(NULL);  
  
   // Instantiate rowset  
   CAuthors rs;  
  
   // Open rowset and move to first row  
   strcpy_s(rs.m_state, sizeof(rs.m_state), _T("CA"));  
   hr = rs.OpenAll();  
   hr = rs.MoveFirst();  
  
   // Iterate through the rowset  
   while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET ) {  
      // Print out the column information for each row  
      printf("First Name: %s, Last Name: %s\n", rs.m_au_fname, rs.m_au_lname);  
      hr = rs.MoveNext();  
   }  
  
   rs.CloseAll();  
   CoUninitialize();  
}  
```  
  
## <a name="example"></a>Příklad  
 Tato ukázka používá `db_source` ve třídě zdroje dat `CMySource`, a `db_command` na třídy příkazů `CCommand1` a `CCommand2`.  
  
```cpp  
// db_command_2.cpp  
// compile with: /c  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
// class usage for both db_source and db_command  
  
[  db_source(L"your connection string"),  
   db_command(L" \  
      SELECT au_lname, au_fname \  
      FROM dbo.authors \  
      WHERE state = 'CA'")  ]  
struct CMySource {  
   HRESULT OpenDataSource() {  
      return S_OK;  
   }  
};  
  
[db_command(command = "SELECT * FROM Products")]  
class CCommand1 {};  
  
[db_command(command = "SELECT FNAME, LNAME FROM Customers")]  
class CCommand2 {};  
  
int main() {  
   CMySource s;  
   HRESULT hr = s.OpenDataSource();  
   if (SUCCEEDED(hr)) {  
      CCommand1 c1;  
      hr = c1.Open(s);  
  
      CCommand2 c2;  
      hr = c2.Open(s);  
   }  
  
   s.CloseDataSource();  
}  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, **struktura**, člen, metoda, místní|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také:  
 [Atributy příjemce technologie OLE DB](../windows/ole-db-consumer-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
