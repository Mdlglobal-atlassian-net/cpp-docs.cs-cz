---
title: Předcházení haldy kolizí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- heap contention
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 731fcb2328f789e5c487dc56510bbd6f7ec049ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="avoidance-of-heap-contention"></a>Předcházení kolizí haldy
Správci řetězec výchozí, poskytované MFC a knihovna ATL jsou jednoduché obálky nad globální haldy. Tato globální halda představuje plně vláken, což znamená, že více vláken můžete přidělit a volné paměti z něj současně bez poškozování halda. Zabezpečení vlákna pomáhají halda má k serializaci přístup na sebe sama. To se obvykle dosahuje kritická sekce nebo podobné uzamčení mechanismu. Vždy, když se dvěma vlákny došlo k pokusu o přístup k haldě současně, jedno vlákno je blokován, dokud dokončení požadavku jiné vlákno. Mnoho aplikací k této situaci dochází zřídka a dopad na výkon uzamčení mechanismu do haldy je nepatrné. Ale pro aplikace, které často halda přístup z více vláken může způsobit kolizí je halda zámek aplikace pomalejší, než pokud by měla jednovláknové (i u počítačů s více procesory).  
  
 Aplikace, které používají [CStringT](../atl-mfc-shared/reference/cstringt-class.md) jsou obzvláště náchylné k haldy kolizí protože operací na `CStringT` objekty často vyžadují opakované přidělení vyrovnávací paměti řetězců.  
  
 Jeden způsob, jak zmírnit haldy kolizí mezi vlákny je tak, aby měl každý podproces přidělit řetězce z haldy privátní, specifická pro přístup z více vláken. Tak dlouho, dokud řetězce přidělené s konkrétní vlákno allocator se používají pouze v daném vláknu, přidělujícího modulu nemusí být bezpečný přístup z více vláken.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje procedury přístup z více vláken, která přiděluje vlastní privátní haldy není bezpečná pro přístup z více vláken pro řetězce v daném vláknu:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/cpp/avoidance-of-heap-contention_1.cpp)]  
  
## <a name="comments"></a>Komentáře  
 Více vláken může být používá stejný postup vlákno ale vzhledem k tomu, že každé vlákno má svou vlastní haldy neexistuje žádné kolizí mezi vlákny. Kromě toho skutečnost, že je každý haldy není bezpečné pro přístup z více vláken dává měřitelné zvýšení výkonu i v případě, že je spuštěna pouze jedna kopie vlákno. Toto je výsledek haldě nepoužíváte nákladné propojené operace pro zajištění ochrany proti souběžný přístup.  
  
 Složitější postup vlákno může být vhodné k uložení ukazatel na řetězec manager vlákna v přihrádce přístup z více vláken místní úložiště (TLS). To umožňuje jiné funkce volané procedurou vlákno pro přístup k manager řetězec vlákna.  
  
## <a name="see-also"></a>Viz také  
 [Správa paměti pomocí CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

