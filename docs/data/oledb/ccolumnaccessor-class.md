---
title: CColumnAccessor – třída | Microsoft Docs
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
ms.openlocfilehash: 8d211277a8354d94f1892b97ea8f808cc0b22c30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095317"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor – třída
Generuje kód vložený příjemce.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CColumnAccessor : public CAccessorBase  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve vloženém kódu každý sloupec je vázána jako samostatné přistupujícího objektu. Je třeba si uvědomit, že tato třída se používá ve vloženém kódu (například se může vyskytne při ladění), ale obvykle není nutné používat ji nebo její metody přímo.  
  
 `CColumnAccessor` implementuje metodu se zakázaným inzerováním, z nichž každý odpovídají ve funkcích do jiných přístupových metod vlastností třídy:  
  
-   `CColumnAccessor` Konstruktor; vytvoří a inicializuje `CColumnAccessor` objektu.  
  
-   `CreateAccessor` Přidělí paměť pro sloupec struktury vazby a inicializuje data členy sloupců.  
  
-   **BindColumns** sváže sloupce přistupující objekty.  
  
-   **SetParameterBuffer** přiděluje vyrovnávací paměti pro parametry.  
  
-   `AddParameter` Přidá položku parametr struktury vstupní parametr.  
  
-   **HasOutputColumns** Určuje, zda má přistupující výstupní sloupce  
  
-   **HasParameters** Určuje, zda má přistupující parametry.  
  
-   `BindParameters` Vytvoří vazbu vytvořený parametry sloupce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)