---
title: Principy (ATL) pro zpracování událostí | Microsoft Docs
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
ms.openlocfilehash: cb7577dc7d9fb58f43ee67d5e5b8f00393dca1bf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355445"
---
# <a name="event-handling-principles"></a>Zásady zpracování událostí
Existují tři kroky společné pro všechny zpracování událostí. Budete muset:  
  
-   Implementaci rozhraní událostí v objektu.  
  
-   Poraďte zdroj události, jestli chce přijímat události objektu.  
  
-   Zdroj události Unadvise, pokud objekt již nepotřebuje přijímat události.  
  
 Způsobem, že budete implementovat rozhraní událostí bude záviset na jeho typu. Události rozhraní může být vtable, duální nebo odesílajícím rozhraním. Je to na návrháře zdroje událostí k definování rozhraní; je to na můžete implementovat dané rozhraní.  
  
> [!NOTE]
>  I když neexistují žádné technické důvody, které nelze duální rozhraní událostí, je počet dobrý návrh důvodů, proč nepoužívejte duals. To je však rozhodnutí provedené designer nebo implementátor události *zdroj*. Vzhledem k tomu, že pracujete z hlediska události `sink`, je nutné povolit pro pravděpodobnost, že je možné, že kdykoli vybíráte, ale k implementaci rozhraní duální události. Další informace o duální rozhraní najdete v tématu [duální rozhraní a knihovna ATL](../atl/dual-interfaces-and-atl.md).  
  
 Poradenství zdroj události lze rozdělit do tří kroků:  
  
-   Dotaz na zdrojový objekt pro [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857).  
  
-   Volání [IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) předávání identifikátory IID rozhraní událost, která vás zajímá. Pokud úspěšné, tato možnost vrátí [IConnectionPoint –](http://msdn.microsoft.com/library/windows/desktop/ms694318) rozhraní na objekt bod připojení.  
  
-   Volání [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) předávání **IUnknown** z jímky událostí. Pokud úspěšné, tato možnost vrátí `DWORD` představující připojení souboru cookie.  
  
 Jakmile úspěšně jste se zaregistrovali váš zájem o příjem událostí, nezavolá se podle události aktivováno objektem zdroje metody pro rozhraní události tohoto objektu. Pokud již nepotřebujete přijímat události, můžete předat souboru cookie zpět do bodu připojení prostřednictvím [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608). Tím dojde k přerušení připojení mezi zdroj a jímka.  
  
 Dávejte pozor, aby se zabránilo odkaz cyklů při zpracování události.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování událostí](../atl/event-handling-and-atl.md)

