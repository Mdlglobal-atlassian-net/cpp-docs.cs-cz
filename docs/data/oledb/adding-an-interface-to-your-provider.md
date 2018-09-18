---
title: Přidání rozhraní ke zprostředkovateli | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f50459550c91f07c12f6f18b3fbbaa5622ab7408
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032390"
---
# <a name="adding-an-interface-to-your-provider"></a>Přidání rozhraní ke zprostředkovateli

Určuje, které objekty chcete přidat rozhraní do (obvykle datové zdroje, sady řádků, příkaz nebo relace objekty vytvořené průvodcem zprostředkovatele OLE DB). Je možné, že objekt je potřeba přidat rozhraní do je ten, který váš poskytovatel v současné době nepodporuje. V takovém případě spusťte ATL OLE DB poskytovatele průvodce k vytvoření objektu. Klikněte pravým tlačítkem na projekt v zobrazení tříd, klikněte na tlačítko **přidat třídu** z **přidat** nabídky a pak klikněte na tlačítko **ATL OLE DB Provider**. Můžete chtít ukládejte kód rozhraní samostatný adresář a potom zkopírujte soubory do projektu poskytovatele.  
  
Pokud jste vytvořili novou třídu pro podporu rozhraní, je objekt, který dědí z třídy. Můžete například přidat třídu **IRowsetIndexImpl** do objektu sady řádků:  
  
```cpp  
template <class Creator>  
class CAgentRowset :   
    public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,  
    public IRowsetIndexImpl< ... >   
```  
  
Přidat rozhraní do **COM_MAP** v objektu COM_INTERFACE_ENTRY – makro. Pokud neexistuje žádná mapa, vytvořte ji. Příklad:  
  
```cpp  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
END_COM_MAP()  
```  
  
U objektu sady řádků řetězu mapu svého nadřazeného objektu objekt tak, aby objekt může delegovat na nadřazenou třídu. V tomto příkladu přidá dané makro COM_INTERFACE_ENTRY_CHAIN do mapy:  
  
```cpp  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)  
END_COM_MAP()  
```  
  
## <a name="see-also"></a>Viz také  

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)