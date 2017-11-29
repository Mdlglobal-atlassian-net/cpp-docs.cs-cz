---
title: "Ukázkový kontejner – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3469645ad62b86b58a30396bbf9af639e392d180
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="sample-container-class"></a>Ukázkový kontejner – třída
> [!NOTE]
>  Toto téma se v dokumentaci k Visual C++ jako funkční příklad kontejnery použít ve standardní knihovně C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).  
  
 Popisuje objekt, který určuje posloupnost různých délka elementy, obvykle typu **Ty**. Pořadí je uložený různými způsoby v závislosti na skutečné kontejneru.  
  
 Kontejner konstruktor nebo člen funkce možná příležitosti k volání konstruktoru **Ty**(**const Ty &**) nebo funkce **Ty::operator =**(**const Ty &**). Pokud volání vyvolá výjimku, objekt kontejneru musí zachovat svou integritu a opětovné všechny výjimky, které zachytávalo. Můžete bezpečně odkládacího souboru, přiřadit k mazání nebo zničit kontejnerového objektu po vyhodí jednu z těchto výjimek. Obecně platí ale nemůžete jinak předpovědět, stav pořadí řízené kontejnerového objektu.  
  
 Několik dalších aspektů:  
  
-   Pokud výraz **~ Ty** vyvolá výjimku, výsledný stav objektu kontejneru není definován.  
  
-   Pokud kontejner obsahuje objekt allocator *al*, a *al* vyvolá výjimku jinak než v důsledku volání *al***.allocate**, výsledný stav objektu kontejneru není definován.  
  
-   Pokud kontejner obsahuje objekt funkce *comp*, určit, jak pořadí řízené sekvenci a *comp* vyvolá výjimku libovolného typu, výsledný stav objektu kontejneru není definován.  
  
 Třídy kontejnerů definované standardní knihovna C++ splnit několik dalších požadavků, jak je popsáno v následujících odstavcích.  
  
 Kontejner – třída šablony [seznamu](../standard-library/list-class.md) poskytuje chování deterministickou a užitečné, ani za přítomnosti výjimky popsané výše. Například pokud je vyvolána výjimka při vkládání do jednoho nebo více elementů kontejneru vlevo v nezměněném stavu a je znovu vyvolány výjimka.  
  
 Pro *všechny* třídy kontejnerů definované standardní knihovna C++, pokud je vyvolána výjimka při volání následující členské funkce:  
  
```  
<A NAME="vclrfcontainerinsert"></A>insert // single element inserted  
<A NAME="vclrfcontainerpushback"></A>push_back  
<A NAME="vclrfcontainerpushfront"></A>push_front  
```  
  
 kontejner je vlevo v nezměněném stavu a je znovu vyvolány výjimku.  
  
 Pro *všechny* kontejneru třídy definované standardní knihovna C++, nedojde k výjimce při volání následující členské funkce:  
  
```  
<A NAME="vclrfcontainerpopback"></A>pop_back  
<A NAME="vclrfcontainerpopfront"></A>pop_front  
```  
  
 Členská funkce [vymazat](../standard-library/container-class-erase.md) vyvolá výjimku, pouze v případě, že operace kopírování (přiřazení nebo kopírování konstrukce) vyvolá výjimku.  
  
 Kromě toho nedojde k výjimce při kopírování iterovat vrácený členské funkce.  
  
 Členská funkce [swap](../standard-library/container-class-swap.md) usnadňuje další lišící *všechny* definované standardní knihovna C++ – třídy kontejnerů:  
  
-   Členská funkce vyvolá výjimku, pouze v případě, že kontejner ukládá al přidělení objektu, a `al` vyvolá výjimku při kopírování.  
  
-   Odkazy, ukazatelů a iterátory, které určit elementy řízené pořadí prohazují jsou dál platné.  
  
 Objekt kontejneru třídy definované standardní knihovna C++ přiděluje a uvolní úložiště pro pořadí jimi řídí prostřednictvím uložené objektu typu `Alloc`, což je obvykle parametr šablony. Takový objekt allocator musí mít stejné externí rozhraní jako objekt třídy **allocator\<Ty >**. Konkrétně `Alloc` musí být stejného typu jako **Alloc::rebind < value_type >:: jiných**  
  
 Pro *všechny* kontejneru tříd definovaných výčtem standardní knihovna C++ – členská funkce **get_allocator – alokační const;** vrátí kopie uložené allocator objektu. Všimněte si, že se objekt uložené allocator *není* zkopírovat, jakmile bude přiřazena kontejnerového objektu. Všechny konstruktory inicializovat s hodnotou uloženou v **allocator**do `Alloc` pokud obsahuje žádný allocator parametr konstruktoru.  
  
 Podle Standard C++ třídu kontejneru definované ve standardní knihovně C++ můžete předpokládat, že:  
  
-   Všechny objekty třídy `Alloc` porovnání rovnosti.  
  
-   Typ **Alloc::const_pointer** je stejný jako **const Ty \*** .  
  
-   Typ **Alloc::const_reference** je stejný jako **const Ty &**.  
  
-   Typ **Alloc::pointer** je stejný jako **Ty \*** .  
  
-   Typ **Alloc::reference** je stejný jako **Ty &**.  
  
 V této implementaci však kontejnery neprovádějte tyto předpoklady. Proto nebudou fungovat správně s allocator objekty, které jsou náročnějších:  
  
-   Všechny objekty třídy `Alloc` nemusí porovnat stejné. (Můžete spravovat více fondů úložiště.)  
  
-   Typ **Alloc::const_pointer** nemusí být stejný jako **const Ty \*** . (Const ukazatel může být třídu).  
  
-   Typ **Alloc::pointer** nemusí být stejný jako **Ty \*** . (Ukazatel může být třídu).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: \<ukázkový kontejner >  
  
## <a name="see-also"></a>Viz také  
 [\<Ukázkový kontejner >](../standard-library/sample-container.md)
