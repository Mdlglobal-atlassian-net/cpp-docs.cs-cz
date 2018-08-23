---
title: Použití ověřitelných sestavení s SQL serverem (C + +/ CLI) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b35675ba0081ec4ea7a1c9559f9a8fb71347cd54
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583816"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>Použití ověřitelných sestavení se serverem SQL Server (C++/CLI)
Rozšířené uložené procedury lze zabalit jako dynamické knihovny (DLL), poskytují způsob, jak rozšířit funkce SQL serveru pomocí funkce byly vyvinuty v sadě Visual C++. Rozšířené uložené procedury jsou implementovány jako funkce uvnitř knihovny DLL. Kromě funkcí, můžete také definujte rozšířené uložené procedury [uživatelem definované typy](../cpp/classes-and-structs-cpp.md) a [agregační funkce](http://msdn.microsoft.com/en-us/de255454-f45e-4281-81f9-bc61893ac5da) (jako je součet a průměr).  
  
 Když klient provede rozšířené uložené procedury, vyhledávání systému SQL Server pro knihovnu DLL přidružené k rozšířené uložené procedury a načte knihovnu DLL. SQL Server volá požadovaný rozšířené uložené procedury a spustí ji v rámci zadaného kontextu zabezpečení. Rozšířená uložená procedura, pak předá sady výsledků a vrátí parametry zpět na server.  
  
 SQL Server poskytuje rozšíření příkazů jazyka Transact-SQL (T-SQL) k tomu, abyste k instalaci ověřitelných sestavení do systému SQL Server. Sada oprávnění systému SQL Server určuje kontext zabezpečení, s následující úrovní zabezpečení:  
  
-   Neomezené režimu: spuštění kódu na vaše vlastní nebezpečí; kód nemusí být prokazatelně typově bezpečný.  
  
-   Nouzový režim: spuštění prokazatelně typově bezpečné kódu; Zkompilovaná/CLR: safe.  
  
 Nouzový režim vyžaduje spuštěné sestavení bude prokazatelně typově bezpečné.  
  
 K vytváření a načítání ověřitelných sestavení do systému SQL Server, použijte příkazy jazyka Transact-SQL příkaz CREATE ASSEMBLY a příkaz DROP ASSEMBLY následujícím způsobem:  
  
```  
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH   
  PERMISSION_SET <permissions>  
DROP ASSEMBLY <assemblyName>  
```  
  
 Příkaz PERMISSION_SET určuje kontext zabezpečení a může mít hodnoty bez omezení, SAFE nebo EXTENDED.  
  
 Kromě toho příkaz CREATE FUNCTION můžete vytvořit vazbu na názvy metod ve třídě:  
  
```  
CREATE FUNCTION <FunctionName>(<FunctionParams>)  
RETURNS returnType  
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]  
```  
  
## <a name="example"></a>Příklad  
 Následující skript SQL (například s názvem "MyScript.sql") načte sestavení do systému SQL Server a zpřístupňuje metodu pro třídu:  
  
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
  
 Skripty SQL lze spustit interaktivně v analyzátoru dotazů SQL nebo na příkazovém řádku pomocí nástroje sqlcmd.exe. Následující příkazový řádek se připojí k MyServer, používá výchozí databázi, používá důvěryhodné připojení, vstupů MyScript.sql a výstup MyResult.txt.  
  
```  
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt  
```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: migrace na/CLR: safe (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
 [Třídy a struktury](../cpp/classes-and-structs-cpp.md)