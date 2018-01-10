---
title: "Podpora volných vláken ve zprostředkovateli | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 14bd61bc4f319a50abdbf76d7f6e60e511e57312
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="supporting-free-threading-in-your-provider"></a>Podpora volných vláken ve zprostředkovateli
Všechny třídy zprostředkovatele OLE DB jsou bezpečné pro přístup z více vláken a položky registru jsou nastaveny odpovídajícím způsobem. Je vhodné podpora volných vláken na pomáhají zajistit vysokou úroveň výkonu v situacích s více uživateli. Zajistit, aby byl váš poskytovatel bezpečné pro přístup z více vláken, musíte ověřit, že je váš kód správně blokován. Při každém zápisu nebo ukládání dat, musíte zablokovat přístup s kritickými oddíly.  
  
 Každý objekt šablony zprostředkovatele technologie OLE DB má své kritické oddíly. Chcete-li blokování snadnější, by měla být každou novou třídu vytvoříte třídu šablony trvá nadřazené třídy jako argument název.  
  
 Následující příklad ukazuje, jak blok kódu:  
  
```  
template <class T>  
class CMyObject<T> : public...  
  
HRESULT MyObject::MyMethod(void)  
{  
   T* pT = (T*)this;      // this gets the parent class   
  
// You don't need to do anything if you are only reading information  
  
// If you want to write information, do the following:  
   pT->Lock();         // engages critical section in the object  
   ...;                // write whatever information you wish  
   pT->Unlock();       // disengages the critical section  
}  
```  
  
 Další informace o tom, jak chránit kritické oddíly s `Lock` a `Unlock`, najdete v části [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
 Musíte také ověřit, že žádné metody přepíšete (například `Execute`) jsou bezpečné pro přístup z více vláken.  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)