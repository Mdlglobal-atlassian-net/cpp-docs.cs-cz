---
title: "Slabé odkazy a ukončování cykly (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a98dc4dd43b40f378a91713770c4c5500c790d0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="weak-references-and-breaking-cycles-ccx"></a>Slabé odkazy a ukončování cykly (C + +/ CX)
V žádné systém typů, který je založen na počítání odkazů, mohl vytvořit odkazy na typy *cykly*– to znamená, jeden objekt odkazuje na druhý objekt, druhý objekt odkazuje na objekt třetí, a tak dále dokud některé konečný objekt odkazuje zpět první objekt. V cyklu nelze odstranit objekty správně při počet odkazů jeden objekt klesne na nulu. Které vám pomůžou vyřešit tento problém, C + +/ CX poskytuje [Platform::WeakReference třída](../cppcx/platform-weakreference-class.md) třídy. A `WeakReference` objektu podporuje [vyřešit](../cppcx/platform-weakreference-class.md#resolve) metoda, která vrátí hodnotu null, pokud objekt již existuje, nebo vyvolá [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) Pokud objekt zachování připojení, ale není typu `T`.  
  
 Jeden scénář, ve kterém `WeakReference` použije je při `this` ukazatel zachytí ve výrazu lambda, který se používá k definování obslužné rutiny události. Doporučujeme použít s názvem metody při definování obslužné rutiny událostí, ale pokud budete chtít použít lambda pro vaše obslužná rutina události – nebo pokud máte pro přerušení odkaz počítání cyklu v některé jiné situaci – použijte `WeakReference`. Tady je příklad:  
  
```  
  
using namespace Platform::Details;  
using namespace Windows::UI::Xaml;  
using namespace Windows::UI::Xaml::Input;  
using namespace Windows::UI::Xaml::Controls;  
  
Class1::Class1()  
{  
    // Class1 has a reference to m_Page  
    m_Page = ref new Page();  
  
    // m_Page will have a reference to this Class1  
    // so create a weak reference to this  
    WeakReference wr(this);  
    m_Page->DoubleTapped += ref new DoubleTappedEventHandler(   
        [wr](Object^ sender, DoubleTappedRoutedEventArgs^ args)  
    {  
       // Use the weak reference to get the object  
       Class1^ c = wr.Resolve<Class1>();  
       if (c != nullptr)  
       {  
           c->m_eventFired = true;  
       }  
       else  
       {  
           // Inform the event that this handler should be removed  
           // from the subscriber list  
           throw ref new DisconnectedException();  
       }  
    });   
}  
  
}  
```  
  
 Když vyvolá obslužnou rutinu události `DisconnectedException`, způsobí, že odebrat ze seznamu odběratele obslužná rutina události.  
  
## <a name="see-also"></a>Viz také  


