---
title: db_table | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.db_table
dev_langs: C++
helpviewer_keywords: db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d2d8c7efaa23a8d7169ca41b4bfcb78722d73543
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dbtable"></a>db_table
Otevře se tabulce OLE DB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ db_table(   
   db_table,   
   name,   
   source_name,   
   hresult   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *db_table –*  
 Řetězec určující název tabulky databáze (například "produkty").  
  
 *název* (volitelné)  
 Název popisovače, který používáte při práci s tabulkou. Pokud chcete vrátit více než jeden řádek výsledků, zadejte tento parametr. **db_table** generuje proměnné se zadaným *název* která lze procházet sadu řádků nebo spustit více dotazů akce.  
  
 *source_name* (volitelné)  
 `CSession` Proměnnou nebo instanci třídy, která má `db_source` atribut použitý k němu na kterém se příkaz provede. V tématu [db_source](../windows/db-source.md).  
  
 `hresult`(volitelné)  
 Určuje proměnné, která se zobrazí `HRESULT` tohoto příkazu databáze. Pokud proměnná neexistuje, ji budou automaticky vloženy atribut.  
  
## <a name="remarks"></a>Poznámky  
 **db_table** vytvoří [CTable](../data/oledb/ctable-class.md) objekt, který je používán příjemce technologie OLE DB se otevřít tabulku. Tento atribut lze použít pouze na úrovni třídy; nemůžete ji použít vložené. Použít **db_column** k vytvoření vazby sloupců tabulky. proměnné; použít **db_param –** pro vymezení (nastavte typ parametru a to na) parametrů.  
  
 Pokud příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor přejmenuje třídy pro \_ *YourClassName*přistupujícího objektu, kde *YourClassName* je název, který jste zadali Třída a kompilátor také vytvoří třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd se zobrazí oba třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad otevře tabulky produktů pro použití `CProducts`.  
  
```  
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
  
 Příklad tohoto atributu se použijí v aplikaci, naleznete v části Ukázky [AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409) a [MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**,`struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy příjemce technologie OLE DB](../windows/ole-db-consumer-attributes.md)   
