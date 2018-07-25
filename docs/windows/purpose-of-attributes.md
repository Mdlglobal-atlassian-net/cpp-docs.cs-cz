---
title: Účel atributů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], about attributes
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ea3b731cc22d144e2e20dc70f14e6b0b76b1479
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877833"
---
# <a name="purpose-of-attributes"></a>Účel atributů
Atributy rozšířit C++ v směrech aktuálně není možné, aniž by vás strukturu classic jazyka. Atributy povolit zprostředkovatele (samostatný DLL) k rozšíření funkčnosti jazyk dynamicky. Primární cílem atributů je zjednodušení vytváření komponenty modelu COM, kromě zvýšit úroveň produktivity vývojáře součásti. Atributy lze použít k téměř všechny C++ konstrukce, jako jsou třídy, datové členy nebo členské funkce. Toto je zvýraznění výhod této nové technologie:  
  
-   Zpřístupní známé a jednoduchý konvence volání.  
  
-   Používá se vloží kód, který na rozdíl od makra, rozpozná ladicího programu.  
  
-   Umožňuje snadno odvození z třídy base bez nákladných implementace podrobnosti.  
  
-   Nahradí velké množství kód IDL vyžadují komponenty modelu COM s několika stručným atributy.  
  
 Například implementovat podřízený jednoduchá událost pro obecné třídy ATL, můžete použít [event_receiver –](../windows/event-receiver.md) atribut určité třídy, jako `CMyReceiver`. **Event_receiver –** atribut je pak zkompilují – kompilátor Visual C++, která vloží správný kód do souboru objektu.  
  
```  
[event_receiver(com)]  
class CMyReceiver   
{  
   void handler1(int i) { ... }  
   void handler2(int i, float j) { ... }  
}  
```  
  
 Potom můžete nastavit **CMyReceiver** metody `handler1` a `handler2` ke zpracování událostí (pomocí funkce vnitřní [__hook](../cpp/hook.md)) ze zdroje událostí, které můžete vytvořit pomocí [event_source –](../windows/event-source.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../windows/attributed-programming-concepts.md)