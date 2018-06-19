---
title: CDataConnection – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 945fed5edd59da93aabb1d22e4830417fc4a2518
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096792"
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
|[Otevřete](../../data/oledb/cdataconnection-open.md)|Otevře připojení ke zdroji dat pomocí inicializačního řetězce.|  
|[Opennewsession –](../../data/oledb/cdataconnection-opennewsession.md)|Otevře novou relaci pro aktuální připojení.|  
  
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