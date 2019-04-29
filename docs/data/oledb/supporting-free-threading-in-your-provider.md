---
title: Podpora volných vláken ve zprostředkovateli
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
ms.openlocfilehash: a2afb7354dd0447375ee6205b7c5d9a4755aa4b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404491"
---
# <a name="supporting-free-threading-in-your-provider"></a>Podpora volných vláken ve zprostředkovateli

Všechny třídy zprostředkovatele OLE DB jsou bezpečné pro vlákna a položky registru se nastaví odpovídajícím způsobem. Je vhodné podpora volných vláken, které vám pomůžou zajistit vysokou úroveň výkonu v situacích s více uživateli. Zajistit, aby byl váš poskytovatel bezpečné pro vlákna, musíte ověřit, že váš kód správně blokované. Při každém zápisu nebo ukládání dat, třeba blokovat přístup s kritických oddílů.

Každý objekt šablony zprostředkovatele OLE DB má svůj vlastní kritický oddíl. Chcete-li snadněji blokování, by měl být každou novou třídu vytvoříte třídu šablony s ohledem na nadřazenou třídu název jako argument.

Následující příklad ukazuje, jak blokovat kódu:

```cpp
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

Další informace o tom, jak chránit kritické oddíly s `Lock` a `Unlock`, naleznete v tématu [Multithreading: Jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

Ověřte, že všechny metody, které přepsat (například `Execute`) jsou bezpečné pro vlákna.

## <a name="see-also"></a>Viz také:

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)