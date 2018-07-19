---
title: Principy (ATL) pro zpracování událostí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 239ea94343652d379048bbeee87d2650d3f1ed72
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852533"
---
# <a name="event-handling-principles"></a>Principy zpracování událostí
Společné pro všechny zpracování událostí jsou tři kroky. Budete muset:  
  
-   Implementace rozhraní události na váš objekt.  
  
-   Doporučte zdroj události, chce přijímat události objektu.  
  
-   Když váš objekt už nebude potřeba příjem událostí, zrušíte avízo o zdroji události.  
  
 Tak, že budete implementovat rozhraní události závisí na jeho typu. Události rozhraní může být vtable, dvou nebo dispinterface. Záleží jen na návrháře k definování rozhraní zdroje událostí To je pro vás k implementaci rozhraní.  
  
> [!NOTE]
>  I když neexistují žádné z technických důvodů, které nelze duální rozhraní události, existuje mnoho důvodů dobrý návrh vyhnout se použití duals. To je však rozhodnutí provedených Návrhář/implementátora události *zdroj*. Vzhledem k tomu, že pracujete z hlediska události `sink`, je nutné povolit možnost, že nemusí mít kdykoli vybíráte, ale implementace rozhraní duální události. Další informace o duální rozhraní najdete v tématu [duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md).  
  
 Nutnost zdroj události je možné rozdělit do tří kroků:  
  
-   Zadat dotaz na objekt zdroje pro [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857).  
  
-   Volání [IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) předávání identifikátor IID rozhraní události, která vás zajímá. Pokud úspěšná, vrátí [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) rozhraní na objekt bodu připojení.  
  
-   Volání [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) předání `IUnknown` z jímky událostí. Pokud úspěšná, vrátí `DWORD` představující připojení souboru cookie.  
  
 Jakmile úspěšně jste se zaregistrovali váš zájem o přijímání událostí, zavolá se podle události vyvolané zdrojový objekt metody rozhraní objektu události. Pokud už nepotřebujete příjem událostí, soubor cookie můžete předat zpět do spojovacího bodu prostřednictvím [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608). Tím dojde k přerušení připojení mezi zdroje a jímky.  
  
 Dejte pozor, abyste se vyhnuli odkaz cykly, při zpracování událostí.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování událostí](../atl/event-handling-and-atl.md)

