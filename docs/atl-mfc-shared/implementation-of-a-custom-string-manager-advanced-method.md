---
title: "Implementace nástroje vlastní řetězec Manager (rozšířené metoda) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e76edc65e5f30fee90f346d5434ecbee320a37a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>Implementace nástroje vlastní řetězec Manager (rozšířené metoda)
V situacích, specializované můžete implementovat vlastní řetězec správce, který mění více než jen haldě, které se používá k přidělení paměti. V takovém případě je nutné ručně implementovat [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) rozhraní jako správce svého vlastní řetězec.  
  
 Chcete-li to provést, je třeba nejprve porozumět jak [CStringT](../atl-mfc-shared/reference/cstringt-class.md) tohoto rozhraní používá ke správě jeho dat řetězce. Všechny instance řetězce `CStringT` má ukazatel [CStringData](../atl-mfc-shared/reference/cstringdata-class.md) struktury. Tato struktura proměnlivou délkou obsahuje důležité informace o řetězce (jako je délka), a také skutečné textových datech řetězce. Každý vlastní řetězec manager zodpovídá za přidělování a uvolnění těchto struktur, na žádost `CStringT`.  
  
 `CStringData` Struktura zahrnuje čtyři pole:  
  
-   [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr) toto pole ukazuje na `IAtlStringMgr` rozhraní sloužící ke správě dat tento řetězec. Když `CStringT` musí přidělit jinému uživateli nebo volné vyrovnávací paměti řetězců zavolá opětovné nebo volné metody tohoto rozhraní předávání `CStringData` struktura jako parametr. Při přidělování `CStringData` struktura v řetězec nadřízeného, je třeba nastavit tak, aby odkazovaly na váš vlastní řetězec manager v tomto poli.  
  
-   [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength) toto pole obsahuje aktuální logické délky řetězce uložené ve vyrovnávací paměti s výjimkou ukončující hodnotu null. `CStringT`Toto pole aktualizuje při délka řetězce. Při přidělování `CStringData` struktura, správce svého řetězec musí nastavit toto pole na nulu. Při opětovném přidělování `CStringData` struktura, vaše vlastní řetězec správce musí zůstat v tomto poli beze změny.  
  
-   [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength) toto pole obsahuje maximální počet znaků (kromě ukončující null), které mohou být uloženy ve vyrovnávací paměti Tento řetězec bez změna přidělování ho. Vždy, když `CStringT` zvýšit logické délky řetězce, je potřeba nejdřív zkontroluje toto pole, abyste měli jistotu, není dostatek místa ve vyrovnávací paměti. Pokud kontrola selže, `CStringT` volání do vaší vlastní řetězec správce a znovu přidělte vyrovnávací paměti. Při přidělování nebo změna přidělování `CStringData` struktura, je potřeba nastavit pole Minimální počet znaků požadovaných v **nChars** parametru [IAtlStringMgr::Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate) nebo [IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate). Pokud existuje více místa ve vyrovnávací paměti, než požadovaná, můžete nastavit tuto hodnotu tak, aby odrážela skutečné množství místa, které jsou k dispozici. To umožňuje `CStringT` růst řetězec k vyplnění celý přidělené místo předtím, než je zpětné volání do správce řetězec a znovu přidělte vyrovnávací paměti.  
  
-   [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs) toto pole obsahuje aktuální počet odkazů vyrovnávací paměti řetězců. Pokud je hodnota jedna a pak jednu instanci `CStringT` používá vyrovnávací paměti. Kromě toho instance je povolena číst a upravovat obsah vyrovnávací paměti. Pokud je hodnota větší než jednu, několik instancí `CStringT` můžete použít vyrovnávací paměti. Protože je sdílen znak vyrovnávací paměť, `CStringT` instance může číst pouze obsah vyrovnávací paměti. Chcete-li upravit obsah, `CStringT` nejprve vytvoří kopii vyrovnávací paměti. Pokud je hodnota záporná, pouze jedna instance `CStringT` používá vyrovnávací paměti. V takovém případě se považuje za vyrovnávací paměti uzamčena. Když `CStringT` instance používá uzamčení vyrovnávací paměti žádné další instance `CStringT` může sdílet vyrovnávací paměti. Tyto instance místo toho vytvoří kopie vyrovnávací paměti před manipulaci s obsahem. Kromě toho `CStringT` instanci pomocí uzamčení vyrovnávací paměti nebude pokoušet o sdílet vyrovnávací paměť jiného `CStringT` přiřazenou instanci. V takovém případě `CStringT` instance zkopíruje jiný řetězec do uzamčení vyrovnávací paměti.  
  
     Při přidělování `CStringData` strukturu, musíte nastavit toto pole tak, aby odrážela typ sdílení, který je povoleno pro velikost vyrovnávací paměti. Pro většinu implementací nastavte tuto hodnotu na jednu. To umožňuje o obvyklé chování sdílení kopírování při zápisu. Pokud váš správce řetězec nepodporuje sdílení řetězce vyrovnávací paměti, ale nastavte pole na uzamčeném stavu. Vynutí se tak `CStringT` pouze používat této vyrovnávací paměti pro instanci `CStringT` které ho přidělilo.  
  
## <a name="see-also"></a>Viz také  
 [Správa paměti pomocí CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

