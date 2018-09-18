---
title: Ccolumnaccessor – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
dev_langs:
- C++
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b1843b6279cb7c86762cc6d975a2a7e67d3d278d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055634"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor – třída

Generuje kód vloženého příjemce.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CColumnAccessor : public CAccessorBase  
```  
  
## <a name="remarks"></a>Poznámky  

Ve vloženém kódu každý sloupec vázaný jako samostatné přistupujícího objektu. Je třeba si uvědomit, že tato třída se používá ve vloženém kódu (například můžete setkat se při ladění), ale obvykle není nutné používat ji nebo její metody přímo.  
  
`CColumnAccessor` implementuje následující metody zástupných procedur, z nichž každý odpovídají funkcí jiným metodám přistupující objekt třídy:  
  
- `CColumnAccessor` Konstruktor; vytvoří a inicializuje `CColumnAccessor` objektu.  
  
- `CreateAccessor` Přiděluje paměť pro sloupec struktury vazby a inicializuje sloupec datové členy.  
  
- `BindColumns` Vytvoří vazbu sloupce přistupující objekty.  
  
- `SetParameterBuffer` Přidělí vyrovnávací paměti pro parametry.  
  
- `AddParameter` Přidá položku parametr struktury vstupní parametr.  
  
- `HasOutputColumns` Určuje, zda má výstup přistupující objekt sloupce  
  
- `HasParameters` Určuje, zda přístupového objektu má parametry.  
  
- `BindParameters` Vytvoří vazbu vytvořené parametry sloupce.  
  
## <a name="requirements"></a>Požadavky  

**Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)