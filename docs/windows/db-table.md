---
title: db_table | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_table
dev_langs:
- C++
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81379a6da96b084239a083bc930cf8e792d518a2
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649748"
---
# <a name="dbtable"></a>db_table
Otevře se tabulku OLE DB.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ db_table(   
   db_table,   
   name,   
   source_name,   
   hresult   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *db_table*  
 Řetězec určující název databázové tabulky (například "produktů").  
  
 *Název* (volitelné)  
 Název popisovače, který slouží pro práci s tabulkou. Tento parametr musíte zadat, pokud se chcete vrátit více než jeden řádek výsledků. **db_table** generuje proměnné se zadaným *název* , který slouží k procházení řádků nebo spustit více dotazů akce.  
  
 *source_name* (volitelné)  
 `CSession` Proměnnou nebo instance třídy, která má `db_source` atribut WebMethod na kterém příkaz spustí. Zobrazit [db_source](../windows/db-source.md).  
  
 *HRESULT* (volitelné)  
 Určuje proměnné, která se zobrazí hodnota HRESULT tohoto databázového příkazu. Pokud proměnná neexistuje, ji budou automaticky vloženy atribut.  
  
## <a name="remarks"></a>Poznámky  
 **db_table** vytvoří [CTable](../data/oledb/ctable-class.md) objekt, který používá příjemce technologie OLE DB otevřít tabulku. Tento atribut lze použít pouze na úrovni třídy; nelze ji použít vložený. Použít `db_column` proměnných, vytvořit vazbu sloupců tabulky použijte `db_param` pro vymezení (nastavený typ parametru a to v) parametrů.  
  
 Když příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor bude přejmenujte třídu na \_ *YourClassName*přístupový objekt, kde *YourClassName* je název, který jste zadali třídy a kompilátor vytvoří také třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd zobrazí se obě třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad otevře tabulky produktů pro použití u `CProducts`.  
  
```cpp  
// db_table.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_table(L"dbo.Products") ]  
class CProducts {  
   [ db_column("1") ] LONG m_ProductID;  
};  
```  
  
 Příklad tohoto atributu použijí v aplikaci, najdete v ukázkách [AtlAgent](http://msdn.microsoft.com/52bef5da-c1a0-4223-b4e6-9e464b6db409) a [MultiRead](http://msdn.microsoft.com/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, **– struktura**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy příjemce technologie OLE DB](../windows/ole-db-consumer-attributes.md)   