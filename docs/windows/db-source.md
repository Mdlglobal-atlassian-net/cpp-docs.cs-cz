---
title: db_source | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b826e5d630b52062892001c26efda01b5c7293f4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873716"
---
# <a name="dbsource"></a>db_source
Vytvoří připojení ke zdroji dat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ db_source(   
   db_source,   
   name,   
   hresult   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *db_source*  
 Připojovací řetězec používaný pro připojení ke zdroji dat. Formát řetězce připojení, najdete v části [připojovací řetězce a Data odkazy](https://msdn.microsoft.com/en-us/library/ms718376.aspx) v Microsoft Data Access Components (MDAC) sady SDK.  
  
 *název* (volitelné)  
 Při použití `db_source` na třídu, *název* je instance objektu zdroje dat, který má `db_source` byt aplikovaný atribut (viz Příklad 1). Při použití `db_source` vložené v implementaci metoda *název* je proměnná (místní počítač do metody), která slouží k přístupu k datům zdroje (viz příklad 2). To předáte *název* k `source_name` parametr **db_command** přidružit zdroji dat pomocí příkazu.  
  
 `hresult` (volitelné)  
 Určuje proměnné, která se zobrazí `HRESULT` tohoto příkazu databáze. Pokud proměnná neexistuje, ji budou automaticky vloženy atribut.  
  
## <a name="remarks"></a>Poznámky  
 `db_source` vytvoří [CDataSource](../data/oledb/cdatasource-class.md) a [CSession](../data/oledb/csession-class.md) objekt, který společně představují připojení ke zdroji dat příjemce technologie OLE DB.  
  
 Při použití `db_source` na třídu, `CSession` objekt stane se členem třídy.  
  
 Při použití `db_source` metoda, bude proveden vloženého kódu v rámci oboru metody a `CSession` objekt se vytvoří jako místní proměnné.  
  
 `db_source` Přidá vlastnosti zdroje dat na třídu nebo v rámci metody. Se používá ve spojení s **db_command** (které trvá `db_source` *název* parametr jako jeho `source_name` parametr).  
  
 Pokud příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor přejmenuje třídy pro \_ *YourClassName*přistupujícího objektu, kde *YourClassName* je název, který jste zadali Třída a kompilátor také vytvoří třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd se zobrazí oba třídy.  
  
 Příklad tohoto atributu se použijí v aplikaci, naleznete v části Ukázky [AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409) a [MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## <a name="example"></a>Příklad  
 Tato ukázka volá `db_source` na třídu vytvořte připojení ke zdroji dat `ds` používá databázi Northwind. `ds` je popisovač pro zdroj dat, který může být použit interně k `CMyCommand` třídy.  
  
```  
// db_source_1.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[  
  db_source(L"my_connection_string", name="ds"),  
  db_command(L"select * from Products")  
]  
class CMyCommand {};  
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
