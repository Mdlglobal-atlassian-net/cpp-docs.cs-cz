---
title: "CFixedStringT: Příklad nástroje vlastní řetězec Manager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords: CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ceb64bb71ad43dd1a6e6fd45a3a0480d68eb643a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT: Příklad nástroje vlastní řetězec Manager
Příkladem manažera vlastní řetězec, který používá třída implementuje knihovny serveru ATL [CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md), volané **CFixedStringMgr**. `CFixedStringT`je odvozený od [CStringT](../atl-mfc-shared/reference/cstringt-class.md) a implementuje řetězec, který přiděluje jeho textová data v rámci `CFixedStringT` samotný objekt tak dlouho, dokud řetězce je menší než délka určeného **t_nChars** parametr šablony `CFixedStringT`. S tímto přístupem řetězec nemusí halda vůbec, není-li délka řetězce zvětšování překračuje velikost vyrovnávací paměti pevné. Protože `CFixedStringT` nemá vždy používání haldy přidělit jeho data řetězec nelze použít **CAtlStringMgr** jako jeho řetězec správce. Používá vlastní řetězec manager (**CFixedStringMgr**), implementující [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) rozhraní. Toto rozhraní je popsána v [implementace nástroje vlastní řetězec Manager (rozšířené metoda)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md).  
  
 V konstruktoru pro **CFixedStringMgr** přijímá tři parametry:  
  
-   **pData:** ukazatel na pevné `CStringData` struktura, který se má použít.  
  
-   **nChars:** maximální počet znaků `CStringData` struktura mohou být uloženy.  
  
-   **pMgr:** ukazatel `IAtlStringMgr` rozhraní "správce zálohování řetězec".  
  
 Konstruktor ukládá hodnoty `pData` a **pMgr** v jejich odpovídajících členské proměnné (`m_pData` a **m_pMgr**). Potom nastaví délka vyrovnávací paměti na nulu, k dispozici délka rovna maximální velikost pevného vyrovnávací paměť a počet odkazů na hodnotu -1. Určuje hodnotu počtu odkazů vyrovnávací paměť je uzamčen a použít tuto instanci **CFixedStringMgr** jako správce řetězec.  
  
 Označení vyrovnávací paměti, protože uzamčení brání dalších `CStringT` instancí z podržíte sdílený odkaz do vyrovnávací paměti. Pokud jiné `CStringT` instance byly povoleny sdílet vyrovnávací paměti by bylo možné pro vyrovnávací paměť obsažený v `CFixedStringT` k odstranění při jiných řetězců stále používáte vyrovnávací paměti.  
  
 **CFixedStringMgr** je úplnou implementaci daného `IAtlStringMgr` rozhraní. Implementace každou metodu je probíraná samostatně.  
  
## <a name="implementation-of-cfixedstringmgrallocate"></a>Implementace CFixedStringMgr::Allocate  
 Implementace **CFixedStringMgr::Allocate** první kontroluje, zda požadovaná velikost řetězce je menší než velikost vyrovnávací paměti pevné (uložené v `m_pData` člen). Pokud pevný vyrovnávací paměť je dostatečně velké **CFixedStringMgr** zamkne pevné vyrovnávací paměti s nulovou délku. Tak dlouho, dokud délka řetězce není nárůst velikosti vyrovnávací paměti pevné, `CStringT` nebudete muset znovu přidělte vyrovnávací paměti.  
  
 Pokud požadovaná velikost řetězce je větší než velikost vyrovnávací paměti pevné **CFixedStringMgr** požadavek předá do správce zálohování řetězec. Správce zálohování řetězec se předpokládá, že přidělit vyrovnávací paměť z haldy. Nicméně před vrácením této vyrovnávací paměti **CFixedStringMgr** uzamkne vyrovnávací paměti a nahradí ukazatel na ukazatel manager řetězec do vyrovnávací paměti **CFixedStringMgr** objektu. To zajistí, která se pokusí přidělit jinému uživateli nebo volné vyrovnávací paměti podle `CStringT` zavolá do **CFixedStringMgr**.  
  
## <a name="implementation-of-cfixedstringmgrreallocate"></a>Implementace CFixedStringMgr::ReAllocate  
 Implementace **CFixedStringMgr::ReAllocate** je velmi podobný jeho implementace **přidělte**.  
  
 Pokud se znovu přidělit vyrovnávací paměť je pevnou velikost vyrovnávací paměti a požadovaná vyrovnávací paměť je menší než velikost vyrovnávací paměti pevné, se provádí žádné přidělení. Ale pokud se znovu přidělit vyrovnávací paměť není pevnou velikost vyrovnávací paměti, musí být vyrovnávací paměť je přiřazen správce zálohování. V takovém případě se používá správce zálohování a znovu přidělte vyrovnávací paměti.  
  
 Pokud se znovu přidělit vyrovnávací paměť je pevnou velikost vyrovnávací paměti a nové vyrovnávací paměť je příliš velký, nevejde se do vyrovnávací paměti pevné, **CFixedStringMgr** přiděluje vyrovnávací paměť nového pomocí správce zálohování. Obsah pevnou velikost vyrovnávací paměti se pak zkopírují do nové vyrovnávací paměti.  
  
## <a name="implementation-of-cfixedstringmgrfree"></a>Implementace CFixedStringMgr::Free  
 Implementace **CFixedStringMgr::Free** používá se stejný vzor jako **přidělte** a `ReAllocate`. Pokud vyrovnávací paměť byla uvolňována pevnou velikost vyrovnávací paměti, metoda ji nastaví na uzamčeném vyrovnávací paměť nulové délky. Pokud vyrovnávací paměť byla uvolňována byl přidělen s správce zálohování **CFixedStringMgr** používá správce zálohování ji uvolnit.  
  
## <a name="implementation-of-cfixedstringmgrclone"></a>Implementace CFixedStringMgr::Clone  
 Implementace **CFixedStringMgr::Clone** vždy vrátí ukazatel do správce zálohování místo **CFixedStringMgr** sám sebe. K tomu dojde, protože všechny instance řetězce **CFixedStringMgr** může být přidružen pouze jednu instanci `CStringT`. Všechny ostatní instance `CStringT` pokusu o klonování Správce by měl získat správce zálohování místo. Je to proto, že správce zálohování podporuje sdílená.  
  
## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>Implementace CFixedStringMgr::GetNilString  
 Implementace **CFixedStringMgr::GetNilString** vrátí pevnou velikost vyrovnávací paměti. Z důvodu očima soulad **CFixedStringMgr** a `CStringT`, dané instanci systému `CStringT` nikdy používá více než jeden vyrovnávací paměti v čase. Proto je ve stejnou dobu potřeba nikdy nulovou hodnotu řetězce a skutečné řetězec vyrovnávací paměti.  
  
 Vždy, když pevné vyrovnávací paměť není používán, **CFixedStringMgr** zajistí, že je inicializován s nulovou délkou. To umožňuje použít jako řetězec s nulovou hodnotu. Jako bonus přidání `nAllocLength` člen pevné vyrovnávací paměti je vždycky nastavený na plnou velikost vyrovnávací paměti pevné. To znamená, že `CStringT` můžou růst řetězec bez volání [IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate), i nulovou hodnotu řetězce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cstringt.h  
  
## <a name="see-also"></a>Viz také  
 [Správa paměti s CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

