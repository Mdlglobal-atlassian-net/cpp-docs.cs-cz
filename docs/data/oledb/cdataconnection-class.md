---
title: "CDataConnection – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
dev_langs:
- C++
helpviewer_keywords:
- CDataConnection class
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2c8e405b95543d170a4e94e39626e9b9793791c7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="cdataconnection-class"></a>CDataConnection – třída
Připojení ke zdroji dat spravuje.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CDataConnection  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CDataConnection](../../data/oledb/cdataconnection-cdataconnection.md)|Konstruktor Vytvoří a inicializuje `CDataConnection` objektu.|  
|[Kopírování](../../data/oledb/cdataconnection-copy.md)|Vytvoří kopii existující datové připojení.|  
|[Open](../../data/oledb/cdataconnection-open.md)|Otevře připojení ke zdroji dat pomocí inicializačního řetězce.|  
|[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)|Otevře novou relaci pro aktuální připojení.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor BOOL](../../data/oledb/cdataconnection-operator-bool.md)|Určuje, zda je aktuální relaci otevřené nebo ne.|  
|[operátor bool](../../data/oledb/cdataconnection-operator-bool-ole-db.md)|Určuje, zda je aktuální relaci otevřené nebo ne.|  
|[operátor CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)|Vrátí odkaz na uzavřeného `CDataSource` objektu.|  
|[CDataSource * – operátor](../../data/oledb/cdataconnection-operator-cdatasource-star.md)|Vrací ukazatel na uzavřeného `CDataSource` objektu.|  
|[operátor CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md)|Vrátí odkaz na uzavřeného `CSession` objektu.|  
|[operátor CSession *](../../data/oledb/cdataconnection-operator-csession-star.md)|Vrací ukazatel na uzavřeného `CSession` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CDataConnection` je užitečné třída pro vytvoření klienty, protože zapouzdřit nezbytných objektů (zdroj dat a relace) a některé úkoly, které musíte udělat při připojování ke zdroji dat  
  
 Bez `CDataConnection`, je nutné vytvořit `CDataSource` objektu, volání jeho [OpenFromInitializationString –](../../data/oledb/cdatasource-openfrominitializationstring.md) metoda, pak vytvořit instanci [CSession](../../data/oledb/csession-class.md) objektu, volání jeho [ Otevřete](../../data/oledb/csession-open.md) metoda, pak vytvořte [CCommand](../../data/oledb/ccommand-class.md) objekt a volání jeho **otevřete*** metody.  
  
 S `CDataConnection`, je třeba pouze vytvořit objekt připojení, předejte ji inicializačního řetězce a pak používat toto připojení otevřete příkazy. Pokud máte v úmyslu používat připojení k databázi opakovaně, je vhodné nechat připojení otevřené, a `CDataConnection` nabízí pohodlný způsob, jak to udělat.  
  
> [!NOTE]
>  Pokud chcete vytvořit databázovou aplikaci, která potřebuje pro zpracování více relací, budete muset použít [opennewsession –](../../data/oledb/cdataconnection-opennewsession.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)