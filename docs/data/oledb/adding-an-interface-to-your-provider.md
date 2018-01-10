---
title: "Přidání rozhraní ke zprostředkovateli | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cd67039848eedc0568e68e1e62f6192b822b9f3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-interface-to-your-provider"></a>Přidání rozhraní ke zprostředkovateli
Určuje, které objekty, které chcete přidat rozhraní (obvykle datové zdroje, řádků, příkaz nebo relace objekty vytvořené průvodcem zprostředkovatele OLE DB). Je možné, že objekt je nutné přidat rozhraní je ten, který váš poskytovatel v současné době nepodporuje. V takovém případě spusťte ATL OLE DB Provider průvodce k vytvoření objektu. Klikněte pravým tlačítkem na projekt v zobrazení tříd, klikněte na tlačítko **přidat třídu** z **přidat** nabídce a pak klikněte na tlačítko **ATL zprostředkovatele technologie OLE DB**. Můžete chtít vložit kód rozhraní v samostatném adresáři a poté zkopírujte soubory do projektu zprostředkovatele.  
  
 Pokud jste vytvořili novou třídu pro podporu rozhraní, je objekt, který dědí z třídy. Může například přidat třídu **IRowsetIndexImpl** do objektu sady řádků:  
  
```  
template <class Creator>  
class CAgentRowset :   
public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,  
   public IRowsetIndexImpl< ... >   
```  
  
 Přidání rozhraní **COM_MAP** v objektu použitím makra COM_INTERFACE_ENTRY. Pokud není mapa, vytvořte. Příklad:  
  
```  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
END_COM_MAP()  
```  
  
 Pro objekt sady řádků řetězu mapy svého nadřazeného objektu tak, aby objekt můžete delegovat na nadřazené třídy. V tomto příkladu přidejte do mapy makro COM_INTERFACE_ENTRY_CHAIN:  
  
```  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)  
END_COM_MAP()  
```  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)