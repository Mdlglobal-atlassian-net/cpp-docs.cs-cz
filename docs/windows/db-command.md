---
title: db_command | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: e0fe3f712566345bb069b798207cfdb10a0aa636
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="dbcommand"></a>db_command
Vytvoří příkaz OLE DB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ db_command(   
   command,   
   name,   
   source_name,   
   hresult,   
   bindings,   
   bulk_fetch)  
]  
```  
  
#### <a name="parameters"></a>Parametry  
 `command`  
 Příkaz řetězec obsahující text příkaz OLE DB. Je jednoduchý příklad:  
  
```  
[ db_command ( command = "Select * from Products" ) ]  
```  
  
 *Příkaz* syntaxe vypadá takto:  
  
```  
binding parameter block 1  
   OLE DB command  
binding parameter block 2  
   continuation of OLE DB command  
binding parameter block 3  
...  
```  
  
 A *bloku parametrů vazby* je definován následujícím způsobem:  
  
 **([** `bindtype` **]** *szVar1* [*, szVar2* [, *nVar3* [,...]]] **)**  
  
 kde:  
  
 **(** označuje začátek datového bloku vazby.  
  
 **[** `bindtype` **]** je jedním z následujících řetězců velká a malá písmena:  
  
-   **[db_column]**  všechny proměnné členů váže ke sloupci v sadě řádků.  
  
-   **[bindto]**  (stejné jako **[db_column]**).  
  
-   **[v]**  váže členské proměnné jako vstupní parametry.  
  
-   **[out]**  váže členské proměnné jako výstupní parametry.  
  
-   **[ve out]**  váže členské proměnné jako vstupní a výstupní parametry.  
  
 *SzVarX* přeloží na členské proměnné v aktuálním oboru.  
  
 **)** označuje konec bloku dat vazby.  
  
 Pokud příkaz řetězec obsahuje jeden nebo více specifikátory například [v], [limit] nebo [vstup/výstup], **db_command** sestavení parametr mapy.  
  
 Pokud příkaz řetězec obsahuje jeden nebo více parametrů, jako je například [db_column] nebo [bindto] **db_command** generuje sadu řádků a mapou přistupujícího objektu ke zpracování těchto vázané proměnné. V tématu [db_accessor](../windows/db-accessor.md) Další informace.  
  
> [!NOTE]
>  [`bindtype`] syntaxe a `bindings` parametru jsou neplatné, při použití **db_command** na úrovni třídy.  
  
 Zde jsou některé příklady vazby parametru bloky. Následující příklad vytvoří vazbu `m_au_fname` a `m_au_lname` datových členů ke `au_fname` a `au_lname` sloupce, respektive z autoři tabulky v databázi pubs:  
  
```  
TCHAR m_au_fname[21];  
TCHAR m_au_lname[41];  
TCHAR m_state[3] = 'CA';  
  
[db_command (  
   command = "SELECT au_fname([bindto]m_au_fname), au_lname([bindto]m_au_lname) " \  
   "FROM dbo.authors " \  
   "WHERE state = ?([in]m_state)")  
```  
  
 ]  
  
 *název* (volitelné)  
 Název popisovače, který používáte pro práci s sadu řádků. Pokud zadáte *název*, **db_command** vygeneruje třídu se zadaným *název*, který může být použit procházení sady řádků nebo provést několik akcí dotazy. Pokud nezadáte *název*, nebude možné vrátit více než jeden řádek výsledky pro uživatele.  
  
 *source_name* (volitelné)  
 `CSession` Proměnnou nebo instanci třídy, která má `db_source` atribut použitý k němu na kterém se příkaz provede. V tématu [db_source](../windows/db-source.md).  
  
 **db_command** kontroluje, ujistěte se, že proměnná používá pro *source_name* je platný, takže by měly mít zadanou proměnnou funkce nebo globální obor.  
  
 `hresult` (volitelné)  
 Určuje proměnné, která se zobrazí `HRESULT` tohoto příkazu databáze. Pokud proměnná neexistuje, ji budou automaticky vloženy atribut.  
  
 *vazby* (volitelné)  
 Umožňuje oddělit vázané parametry z příkazu OLE DB.  
  
 Pokud zadáte hodnotu `bindings`, **db_command** provede analýzu přidružená hodnota a nebude analyzovat [`bindtype`] parametr. Toto použití umožňuje použijte syntaxi zprostředkovatele OLE DB. Pokud chcete zakázat analýza bez vazby parametrů, zadejte **vazby = ""**.  
  
 Pokud nezadáte hodnotu `bindings`, **db_command** provede analýzu bloku vazby parametrů, hledá se **(**", za nímž následují **[** `bindtype` **]**  v závorkách, za nímž následuje jeden nebo více dříve deklarované C++ členské proměnné, následuje '**)**'. Veškerého textu v závorkách se odstraní z výsledné příkazu a tyto parametry se použije ke konstrukci sloupce a parametr vazby pro tento příkaz.  
  
 *bulk_fetch*(volitelné)  
 Celočíselná hodnota, která určuje počet řádků, které mají načíst.  
  
 Výchozí hodnota je 1, který určuje načítání jeden řádek (sada řádků bude typu [CRowset](../data/oledb/crowset-class.md)).  
  
 Hodnota, která je vyšší než 1 představuje hromadné načítání řádků. Hromadné načítání řádků odkazuje hromadné sady řádků schopnost zpracovávat načítání několika řádků (sada řádků bude typu [CBulkRowset](../data/oledb/cbulkrowset-class.md) a zavolá `SetRows` s zadaný počet řádků).  
  
 Pokud *bulk_fetch* je menší než 1, `SetRows` vrátí nula.  
  
## <a name="remarks"></a>Poznámky  
 **db_command** vytvoří [CCommand](../data/oledb/ccommand-class.md) objekt, který je používán příjemce technologie OLE DB k provedení příkazu.  
  
 Můžete použít **db_command** s rozsahem třídy nebo funkce; Hlavní rozdíl spočívá působnosti `CCommand` objektu. Pomocí funkce oboru data, jako jsou třeba vazby ukončit na konci funkce. Použití oboru třídy a funkce zahrnují šablony příjemce technologie OLE DB – třída **CCommand <>**, ale šablony argumenty, které se liší v případech funkce a třída. V případě funkce budou provedeny vazby **přistupujícího objektu** místní proměnné, které zahrnuje při použití třídy odvodí `CAccessor`-odvozené třídy jako argument. Když se použije jako atribut třídy **db_command** funguje ve spojení s **db_column**.  
  
 **db_command** můžete použít ke spuštění příkazů, které nevracejí je sada výsledků dotazu.  
  
 Pokud příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor přejmenuje třídy pro \_ *YourClassName*přistupujícího objektu, kde *YourClassName* je název, který jste zadali Třída a kompilátor také vytvoří třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd se zobrazí oba třídy.  
  
## <a name="example"></a>Příklad  
 Tento příklad definuje příkaz, který vybere první a poslední názvy z tabulky, kde sloupci stavu odpovídá "CA". **db_command** vytvoří a načte sadu řádků, na kterém bude možné volat generované v Průvodci funkce, jako [OpenAll a CloseAll](../data/oledb/consumer-wizard-generated-methods.md), a také `CRowset` členské funkce, jako [MoveNext](../data/oledb/crowset-movenext.md).  
  
 Všimněte si, že tento kód musíte zadat vlastní připojovací řetězec, který se připojuje k databázi pubs. Informace o tom, jak to udělat ve vývojovém prostředí najdete v tématu [postupy: připojení k databázi z Průzkumníka serveru](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74) a [postupy: přidání nových připojení dat v Průzkumníku serveru Průzkumníka a databáze](http://msdn.microsoft.com/en-us/fb2f513b-ddad-4142-911e-856bba0054c8).  
  
```  
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
  
```  
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
 V tomto příkladu `db_source` na zdrojovou třídu dat `CMySource`, a `db_command` na třídy příkazů `CCommand1` a `CCommand2`.  
  
```  
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
|**Platí pro**|**Třída**, `struct`, člen, metoda, místní|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy příjemce technologie OLE DB](../windows/ole-db-consumer-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
