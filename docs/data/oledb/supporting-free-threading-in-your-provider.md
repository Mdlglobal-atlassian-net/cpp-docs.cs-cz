---
title: Podpora volných vláken ve zprostředkovateli
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
ms.openlocfilehash: 50e05b70a782dd343031443540790697e980c994
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209536"
---
# <a name="supporting-free-threading-in-your-provider"></a>Podpora volných vláken ve zprostředkovateli

Všechny třídy poskytovatele OLE DB jsou bezpečné pro přístup z více vláken a položky registru jsou nastaveny odpovídajícím způsobem. Pro zajištění vysoké úrovně výkonu v situacích s více uživateli je vhodné podporovat bezplatná vlákna. Aby bylo možné zajistit bezpečnost pro přístup z více vláken, je nutné ověřit, zda je kód správně zablokován. Kdykoli zapisujete nebo ukládáte data, je nutné zablokovat přístup s kritickými oddíly.

Každý objekt šablony poskytovatele OLE DB má svůj vlastní kritický oddíl. Aby bylo blokování snazší, každá nová třída, kterou vytvoříte, by měla být třída šablony, která přebírá název nadřazené třídy jako argument.

Následující příklad ukazuje, jak zablokovat váš kód:

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

Další informace o tom, jak chránit kritické oddíly pomocí `Lock` a `Unlock`, naleznete v tématu [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

Ověřte, že všechny metody, které přepisujete (například `Execute`), jsou bezpečné pro přístup z více vláken.

## <a name="see-also"></a>Viz také

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
