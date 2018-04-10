---
title: Použití ověřitelných sestavení se serverem SQL Server (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d03d54dd52f95f3fbba35bb896594e90aa92e867
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>Použití ověřitelných sestavení se serverem SQL Server (C++/CLI)
Rozšířené uložené procedury jsou reprezentovány jako dynamické knihovny (DLL), poskytují způsob, jak rozšířit funkce SQL Server pomocí funkcí vytvořených s Visual C++. Rozšířené uložené procedury jsou implementovány jako funkce uvnitř knihovny DLL. Kromě funkcí, můžete také definovat rozšířené uložené procedury [uživatelem definované typy](../cpp/classes-and-structs-cpp.md) a [agregační funkce](http://msdn.microsoft.com/en-us/de255454-f45e-4281-81f9-bc61893ac5da) (například SUMA nebo průměr).  
  
 Když klient provede rozšířenou uloženou proceduru, vyhledávání systému SQL Server pro knihovnu DLL přidružené rozšířené uložené procedury a knihovnu DLL načte. SQL Server volá požadovaný rozšířené uložené procedury a spustí ji v rámci zadaného kontextu zabezpečení. Rozšířená uložená procedura pak předá sady výsledků a vrátí parametry zpět na server.  
  
 [!INCLUDE[sqprsqlong](../dotnet/includes/sqprsqlong_md.md)]Poskytuje rozšíření Transact-SQL (T-SQL) aby bylo možné instalovat ověřitelná sestavení do systému SQL Server. Sada oprávnění serveru SQL určuje kontext zabezpečení, s následujícími úrovněmi zabezpečení:  
  
-   Neomezený režim: spuštění kódu na vlastní nebezpečí; jako typ ověřitelný kód nemá.  
  
-   Nouzový režim: spustit zajišťující bezpečnost ověřitelný kód; Kompilovat s/clr: safe.  
  
 Nouzový režim vyžaduje spuštění sestavení, které chcete být ověřitelný zajišťující bezpečnost.  
  
 Vytvoření a načtení ověřitelná sestavení do systému SQL Server, použijte příkazy jazyka Transact-SQL vytvořit sestavení a DROP ASSEMBLY takto:  
  
```  
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH   
  PERMISSION_SET <permissions>  
DROP ASSEMBLY <assemblyName>  
```  
  
 Příkaz PERMISSION_SET určuje kontext zabezpečení a může mít hodnoty bez omezení, BEZPEČNÉ nebo rozšířené.  
  
 Kromě toho můžete příkaz CREATE FUNCTION se vytvořit vazbu na názvy metod ve třídě:  
  
```  
CREATE FUNCTION <FunctionName>(<FunctionParams>)  
RETURNS returnType  
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]  
```  
  
## <a name="example"></a>Příklad  
 Následující skript SQL (například s názvem "MyScript.sql") načte sestavení do systému SQL Server a zpřístupní metodu třídy:  
  
```  
-- Create assembly without external access  
drop assembly stockNoEA  
go  
create assembly stockNoEA  
from   
'c:\stockNoEA.dll'  
with permission_set safe  
  
-- Create function on assembly with no external access  
drop function GetQuoteNoEA  
go  
create function GetQuoteNoEA(@sym nvarchar(10))  
returns real  
external name stockNoEA:StockQuotes::GetQuote  
go  
  
-- To call the function  
select dbo.GetQuoteNoEA('MSFT')  
go  
```  
  
 Skripty SQL můžete provedeny interaktivně v analyzátoru dotazů SQL nebo na příkazovém řádku pomocí nástroje sqlcmd.exe. Následující příkazový řádek se připojuje k MyServer, používá výchozí databáze, důvěryhodné připojení, vstup MyScript.sql a výstup MyResult.txt.  
  
```  
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt  
```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: migrace na/CLR: safe (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
 [Třídy a struktury](../cpp/classes-and-structs-cpp.md)